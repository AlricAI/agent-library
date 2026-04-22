---
name: Dsl Ebnf
description: Purpose: simple, LLM-friendly grammar that compiles to a RETE IR.
model: claude-sonnet-4-5
---
# Epona Rules DSL — EBNF (v0)

Purpose: simple, LLM-friendly grammar that compiles to a RETE IR. No user-defined functions in v0.

## Grammar (EBNF)

```ebnf
program        ::= { rule }

rule           ::= "rule" string_lit [ "salience:" integer ] "do"
                   "when" newline
                   when_block
                   "then" newline
                   then_block
                   "end"

when_block     ::= { (fact_pattern | guard_stmt) newline }

fact_pattern   ::= binding ":" type_name "(" field_match { "," field_match } ")"
                 | type_name "(" field_match { "," field_match } ")"

binding        ::= ident
type_name      ::= ident

field_match    ::= ident ":" match_expr

match_expr     ::= literal
                 | binding_ref
                 | "_"                                 (*wildcard*)
                 | comparison_expr
                 | set_expr

comparison_expr::= value_expr comp_op value_expr
comp_op        ::= "==" | "!=" | ">" | ">=" | "<" | "<="

set_expr       ::= binding_ref "in" "[" value_list "]"
                 | binding_ref "not_in" "[" value_list "]"

value_list     ::= value_expr { "," value_expr }

value_expr     ::= literal | binding_ref | arithmetic_expr
arithmetic_expr::= value_expr arith_op value_expr
arith_op       ::= "+" | "-" | "*" | "/"

binding_ref    ::= ident

guard_stmt     ::= "guard" guard_expr
guard_expr     ::= comparison_expr
                 | set_expr
                 | between_expr
                 | logical_expr

between_expr   ::= value_expr "between" value_expr "and" value_expr

logical_expr   ::= guard_term { logical_op guard_term }
guard_term     ::= "(" guard_expr ")" | comparison_expr | set_expr | between_expr
logical_op     ::= "and" | "or"

then_block     ::= { action_stmt newline }
action_stmt    ::= "emit" type_name "(" field_assign { "," field_assign } ")"
field_assign   ::= ident ":" value_expr

literal        ::= string_lit | number_lit | bool_lit | date_lit | datetime_lit

string_lit     ::= '"' { char_no_quote | '\"' } '"'
number_lit     ::= ["-"] digit { digit } [ "." digit { digit } ]
bool_lit       ::= "true" | "false"
date_lit       ::= "D" "'" yyyy "-" mm "-" dd "'"
datetime_lit   ::= "DT" "'" yyyy "-" mm "-" dd "T" hh ":" mi [ ":" ss ] "Z" "'"

ident          ::= letter { letter | digit | "_" }
digit          ::= "0" | "1" | ... | "9"
letter         ::= "A" | ... | "Z" | "a" | ... | "z"

newline        ::= ( "\n" | "\r\n" )
yyyy           ::= digit digit digit digit
mm             ::= digit digit
dd             ::= digit digit
hh             ::= digit digit
mi             ::= digit digit
ss             ::= digit digit
```

## Examples

```dsl
rule "overtime-threshold" salience: 10 do
  when
    ts: Timesheet(employee_id: e, hours: h, date: d)
    contract: Contract(employee_id: e, overtime_rate: r)
    guard h > 40 and D'2025-01-01' <= d
  then
    emit Decision(type: "overtime_due", employee_id: e, overtime_hours: h - 40, rate: r)
end

rule "minimum-wage" do
  when
    shift: Shift(employee_id: e, hours: h, hourly_rate: w, date: d, jurisdiction: j)
    law: Jurisdiction(code: j, min_wage: m)
    guard w < m and d between D'2025-01-01' and D'2025-12-31'
  then
    emit ComplianceViolation(kind: "min_wage_breach", employee_id: e, deficit_per_hour: m - w)
end
```