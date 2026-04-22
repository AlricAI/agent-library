# Test Issues

> ## Warnings discovered in /blockers/

================================================================================================================

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Issues discovered while testing the full codebase

## Warnings discovered in /blockers/

============================================================================================================================================================================================================== warnings summary ===============================================================================================================================================================================================================
codeframe/agents/test_worker_agent.py:25
  /home/frankbria/projects/codeframe/codeframe/agents/test_worker_agent.py:25: PytestCollectionWarning: cannot collect test class 'TestWorkerAgent' because it has a __init__ constructor (from: tests/blockers/test_blocker_answer_injection.py)
    class TestWorkerAgent(WorkerAgent):

codeframe/agents/test_worker_agent.py:25
  /home/frankbria/projects/codeframe/codeframe/agents/test_worker_agent.py:25: PytestCollectionWarning: cannot collect test class 'TestWorkerAgent' because it has a __init__ constructor (from: tests/blockers/test_blocker_type_validation.py)
    class TestWorkerAgent(WorkerAgent):

codeframe/agents/test_worker_agent.py:25
  /home/frankbria/projects/codeframe/codeframe/agents/test_worker_agent.py:25: PytestCollectionWarning: cannot collect test class 'TestWorkerAgent' because it has a __init__ constructor (from: tests/blockers/test_wait_for_blocker_resolution.py)
    class TestWorkerAgent(WorkerAgent):

tests/blockers/test_blockers.py::TestDuplicateResolution::test_concurrent_resolution_race_condition
  /home/frankbria/projects/codeframe/.venv/lib/python3.13/site-packages/_pytest/threadexception.py:58: PytestUnhandledThreadExceptionWarning: Exception in thread Thread-1 (resolve_a)
  
  Traceback (most recent call last):
    File "/home/frankbria/.local/share/uv/python/cpython-3.13.5-linux-x86_64-gnu/lib/python3.13/threading.py", line 1043, in _bootstrap_inner
      self.run()
      ~~~~~~~~^^
    

*[truncated — see source for full prompt]*