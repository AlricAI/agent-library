#  Redaction

> """Shared redaction utilities for middleware components.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Shared redaction utilities for middleware components."""

from __future__ import annotations

import hashlib
import ipaddress
import operator
import re
from collections.abc import Callable, Sequence
from dataclasses import dataclass
from typing import Literal
from urllib.parse import urlparse

from typing_extensions import TypedDict

RedactionStrategy = Literal["block", "redact", "mask", "hash"]
"""Supported strategies for handling detected sensitive values."""


class PIIMatch(TypedDict):
    """Represents an individual match of sensitive data."""

    type: str
    value: str
    start: int
    end: int


class PIIDetectionError(Exception):
    """Raised when configured to block on detected sensitive values."""

    def __init__(self, pii_type: str, matches: Sequence[PIIMatch]) -> None:
        """Initialize the exception with match context.

        Args:
            pii_type: Name of the detected sensitive type.
            matches: All matches that were detected for that type.
        """
        self.pii_type = pii_type
        self.matches = list(matches)
        count = len(matches)
        msg = f"Detected {count} instance(s) of {pii_type} in text content"
        super().__init__(msg)


Detector = Callable[[str], list[PIIMatch]]
"""Callable signature for detectors that locate sensitive values."""


def detect_email(content: str) -> list[PIIMatch]:
    """Detect email addresses in content.

    Args:
        content: The text content to scan for email addresses.

    Returns:
        A list of detected email matches.
    """
    pattern = r"\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b"
    return [
        PIIMatch(
            type="email",
            value=match.group(),
            start=match.start(),
            end=match.end(),
        )
        for match in re.finditer(pattern, content)
    ]


def detect_credit_card(content: str) -> list[PIIMatch]:
    """Detect credit card numbers in content using Luhn validation.

    Args:
        cont

*[truncated — see source for full prompt]*