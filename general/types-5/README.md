#  Types

> from typing import Any, Dict, List, TypedDict, Union

from autogen_core import FunctionCall, Image
from autogen_core.models import FunctionExecutionRe

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import Any, Dict, List, TypedDict, Union

from autogen_core import FunctionCall, Image
from autogen_core.models import FunctionExecutionResult

UserContent = Union[str, List[Union[str, Image]]]
AssistantContent = Union[str, List[FunctionCall]]
FunctionExecutionContent = List[FunctionExecutionResult]
SystemContent = str


class DOMRectangle(TypedDict):
    x: Union[int, float]
    y: Union[int, float]
    width: Union[int, float]
    height: Union[int, float]
    top: Union[int, float]
    right: Union[int, float]
    bottom: Union[int, float]
    left: Union[int, float]


class VisualViewport(TypedDict):
    height: Union[int, float]
    width: Union[int, float]
    offsetLeft: Union[int, float]
    offsetTop: Union[int, float]
    pageLeft: Union[int, float]
    pageTop: Union[int, float]
    scale: Union[int, float]
    clientWidth: Union[int, float]
    clientHeight: Union[int, float]
    scrollWidth: Union[int, float]
    scrollHeight: Union[int, float]


class InteractiveRegion(TypedDict):
    tag_name: str
    role: str
    aria_name: str
    v_scrollable: bool
    rects: List[DOMRectangle]


# Helper functions for dealing with JSON. Not sure there's a better way?


def _get_str(d: Any, k: str) -> str:
    val = d[k]
    assert isinstance(val, str)
    return val


def _get_number(d: Any, k: str) -> Union[int, float]:
    val = d[k]
    assert isinstance(val, int) or isinstance(val, float)
    return val


def _get_bool(d: Any, k: str) -> bool:
    val = d[k]
    assert isinstance(val, bool)
    return val


def domrectangle_from_dict(rect: Dict[str, Any]) -> DOMRectangle:
    return DOMRectangle(
        x=_get_number(rect, "x"),
        y=_get_number(rect, "y"),
        width=_get_number(rect, "width"),
        height=_get_number(rect, "height"),
        top=_get_number(rect, "top"),
        right=_get_number(rect, "right"),
        bottom=_get_number(rect, "bottom"),
        left=_get_number(rect, "left"),
    )


def interactiveregion_from_dict

*[truncated — see source for full prompt]*