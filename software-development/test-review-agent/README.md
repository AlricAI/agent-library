# Test Review Agent

> """Tests for Review Agent (Sprint 10 - US-1).

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for Review Agent (Sprint 10 - US-1).

Following TDD: These tests are written BEFORE implementation.
Expected result: ALL TESTS FAIL (RED phase) until ReviewAgent is implemented.
"""

import pytest
from codeframe.core.models import (
    Task,
    TaskStatus,
    CodeReview,
    Severity,
    ReviewCategory,
)
from codeframe.persistence.database import Database


@pytest.fixture
def db():
    """Create a test database in memory."""
    database = Database(":memory:")
    database.initialize()

    # Create test project
    cursor = database.conn.cursor()
    cursor.execute(
        "INSERT INTO projects (name, description, workspace_path, status) VALUES (?, ?, ?, ?)",
        ("test-project", "Test project", "/tmp/test", "active"),
    )
    database.conn.commit()

    return database


@pytest.fixture
def sample_code_with_sql_injection():
    """Sample code with SQL injection vulnerability for testing."""
    return '''
def get_user(username):
    """Get user from database - VULNERABLE!"""
    query = f"SELECT * FROM users WHERE username = '{username}'"
    cursor.execute(query)
    return cursor.fetchone()
'''


@pytest.fixture
def sample_code_with_performance_issue():
    """Sample code with O(n²) performance issue."""
    return '''
def find_duplicates(items):
    """Find duplicate items - SLOW O(n²) algorithm!"""
    duplicates = []
    for i in range(len(items)):
        for j in range(i + 1, len(items)):
            if items[i] == items[j]:
                duplicates.append(items[i])
    return duplicates
'''


@pytest.fixture
def sample_task_with_code(db, sample_code_with_sql_injection):
    """Create a task with code files for review."""
    # Create an issue first (required by foreign key)
    from codeframe.core.models import Issue

    issue = Issue(
        project_id=1,
        issue_number="1.1",
        title="User Management",
        status=TaskStatus.IN_PROGRESS,
        priority=0,
        workflow_step=1,
    )
    issue_id = db.create_i

*[truncated — see source for full prompt]*