#  Markdown File Browser

> import datetime
import io
import os
import re
import time
from typing import List, Optional, Tuple, Union

# TODO: Fix unfollowed import
from markitdo

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ruff: noqa: E722
import datetime
import io
import os
import re
import time
from typing import List, Optional, Tuple, Union

# TODO: Fix unfollowed import
from markitdown import FileConversionException, MarkItDown, UnsupportedFormatException  # type: ignore


class MarkdownFileBrowser:
    """
    (In preview) An extremely simple Markdown-powered file browser.
    """

    # TODO: Fix unfollowed import
    def __init__(  # type: ignore
        self,
        viewport_size: Union[int, None] = 1024 * 8,
        base_path: str | None = os.getcwd(),
        cwd: str | None = None,
    ):
        """
        Instantiate a new MarkdownFileBrowser.

        Arguments:
            viewport_size: Approximately how many *characters* fit in the viewport. Viewport dimensions are adjusted dynamically to avoid cutting off words (default: 8192).
            base_path: The base path to use for the file browser. Files outside this path cannot be accessed. Defaults to the current working directory.
            cwd: The browser's current working directory. Defaults to the system's current working directory.
        """
        self.viewport_size = viewport_size  # Applies only to the standard uri types
        self.history: List[Tuple[str, float]] = list()
        self.page_title: Optional[str] = None
        self.viewport_current_page = 0
        self.viewport_pages: List[Tuple[int, int]] = list()
        self._markdown_converter = MarkItDown()
        self._base_path = None if base_path is None else os.path.realpath(base_path)
        self._page_content: str = ""
        self._find_on_page_query: Union[str, None] = None
        self._find_on_page_last_result: Union[int, None] = None  # Location of the last result

        # Set the working directory
        if cwd is None:
            if self._validate_path(os.getcwd()):
                # Use the current working directory if it's in the base path
                cwd = os.path.realpath(os.getcwd())
            elif self._base_path is

*[truncated — see source for full prompt]*