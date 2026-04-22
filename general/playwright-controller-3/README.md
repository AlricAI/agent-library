# Playwright Controller

> import asyncio
import base64
import io
import os
import random
import warnings
from types import ModuleType
from typing import Any, Callable, Dict, Op

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import asyncio
import base64
import io
import os
import random
import warnings
from types import ModuleType
from typing import Any, Callable, Dict, Optional, Tuple, Union, cast

from playwright._impl._errors import Error as PlaywrightError
from playwright._impl._errors import TimeoutError
from playwright.async_api import Download, Page

from ._types import (
    InteractiveRegion,
    VisualViewport,
    interactiveregion_from_dict,
    visualviewport_from_dict,
)

markitdown: ModuleType | None = None
try:
    # Suppress warnings from markitdown -- which is pretty chatty
    warnings.filterwarnings(action="ignore", module="markitdown")
    import markitdown
except ImportError:
    pass


class PlaywrightController:
    """
    A helper class to allow Playwright to interact with web pages to perform actions such as clicking, filling, and scrolling.

    Args:
        downloads_folder (str | None): The folder to save downloads to. If None, downloads are not saved.
        animate_actions (bool): Whether to animate the actions (create fake cursor to click).
        viewport_width (int): The width of the viewport.
        viewport_height (int): The height of the viewport.
        _download_handler (Optional[Callable[[Download], None]]): A function to handle downloads.
        to_resize_viewport (bool): Whether to resize the viewport
    """

    def __init__(
        self,
        downloads_folder: str | None = None,
        animate_actions: bool = False,
        viewport_width: int = 1440,
        viewport_height: int = 900,
        _download_handler: Optional[Callable[[Download], None]] = None,
        to_resize_viewport: bool = True,
    ) -> None:
        """
        Initialize the PlaywrightController.
        """
        assert isinstance(animate_actions, bool)
        assert isinstance(viewport_width, int)
        assert isinstance(viewport_height, int)
        assert viewport_height > 0
        assert viewport_width > 0

        self.animate_actions = animate_ac

*[truncated — see source for full prompt]*