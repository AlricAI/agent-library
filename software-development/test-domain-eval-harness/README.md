# Test Domain Eval Harness

> """Tests for the DomainEvalHarness.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Tests for the DomainEvalHarness."""

from __future__ import annotations

from amplihack.agents.domain_agents.code_review.agent import CodeReviewAgent
from amplihack.agents.domain_agents.meeting_synthesizer.agent import MeetingSynthesizerAgent
from amplihack.eval.domain_eval_harness import DomainEvalHarness, EvalReport


class TestDomainEvalHarnessCodeReview:
    """Test eval harness with CodeReviewAgent."""

    def test_run_all_levels(self):
        agent = CodeReviewAgent("test_reviewer")
        harness = DomainEvalHarness(agent)
        report = harness.run()

        assert isinstance(report, EvalReport)
        assert report.agent_name == "test_reviewer"
        assert report.domain == "code_review"
        assert len(report.levels) == 4
        assert 0.0 <= report.overall_score <= 1.0

    def test_run_single_level(self):
        agent = CodeReviewAgent("test_reviewer")
        harness = DomainEvalHarness(agent)
        report = harness.run(levels=["L1"])

        assert len(report.levels) == 1
        assert report.levels[0].level_id == "L1"

    def test_run_multiple_levels(self):
        agent = CodeReviewAgent("test_reviewer")
        harness = DomainEvalHarness(agent)
        report = harness.run(levels=["L1", "L2"])

        assert len(report.levels) == 2

    def test_l1_basic_detection(self):
        agent = CodeReviewAgent("test_reviewer")
        harness = DomainEvalHarness(agent)
        report = harness.run(levels=["L1"])

        l1 = report.levels[0]
        assert l1.level_id == "L1"
        assert len(l1.scenarios) >= 2
        # Agent should detect at least some basic bugs
        assert l1.average_score > 0.0

    def test_l3_security_review(self):
        agent = CodeReviewAgent("test_reviewer")
        harness = DomainEvalHarness(agent)
        report = harness.run(levels=["L3"])

        l3 = report.levels[0]
        assert l3.level_id == "L3"
        # Security issues should be detected by the tools
        assert l3.average_score > 

*[truncated — see source for full prompt]*