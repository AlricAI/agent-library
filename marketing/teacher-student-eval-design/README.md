# TEACHER STUDENT EVAL DESIGN

> ## For: Next session colleague designing the two-agent eval

## Goal

Design an evaluation harness where **Agent A (Teacher)** learns content with the

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Teacher-Student Learning Evaluation Design Brief

## For: Next session colleague designing the two-agent eval

## Goal

Design an evaluation harness where **Agent A (Teacher)** learns content with the goal of teaching it, then interacts with **Agent B (Student)** who must demonstrate understanding. We measure how well the Student learned, which reflects how well the Teacher taught.

## Why This Matters

Current eval tests whether an agent can recall facts. But real learning means being able to:

- Explain concepts to someone else (Feynman's "teach to learn")
- Adapt explanations based on the learner's understanding
- Organize knowledge into a teachable structure
- Assess whether the student actually understood

This is a much harder test than recall - it evaluates the agent's ability to **organize and communicate** knowledge, not just store and retrieve it.

## Workflow (Exact Sequence)

```
Step 1: Build prompt for general-purpose learning and teaching agent
  → Write prompt.md describing the agent's goal

Step 2: Generate teacher agent via goal-seeking agent generator
  → amplihack new --file teacher_prompt.md --enable-memory
  → Produces teacher agent with HierarchicalMemory, Graph RAG, intent detection

Step 3: Teacher agent learns content (initial learning)
  → Teacher reads content, stores in its own Kuzu DB
  → Teacher's memory: ~/.amplihack/memory/teacher_{session}/kuzu_db

Step 4: Evaluate teacher's learning
  → Run quiz against teacher to verify it learned the material
  → Must pass L1-L4 thresholds before proceeding to teach

Step 5: Generate student agent via goal-seeking agent generator
  → amplihack new --file student_prompt.md --enable-memory
  → Produces student agent with SEPARATE empty Kuzu DB
  → Student's memory: ~/.amplihack/memory/student_{session}/kuzu_db

Step 6: Teaching session (teacher teaches student)
  → Multi-turn conversation between teacher and student
  → Teacher retrieves from ITS memory, explains to student
  → Student stores wha

*[truncated — see source for full prompt]*