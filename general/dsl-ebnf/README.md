# Dsl Ebnf

> Purpose: simple, LLM-friendly grammar that compiles to a RETE IR.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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

st

*[truncated — see source for full prompt]*