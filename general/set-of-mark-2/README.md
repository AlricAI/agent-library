#  Set Of Mark

> import io
import random
from typing import BinaryIO, Dict, List, Tuple, cast

from PIL import Image, ImageDraw, ImageFont

from ._types import DOMRect

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import io
import random
from typing import BinaryIO, Dict, List, Tuple, cast

from PIL import Image, ImageDraw, ImageFont

from ._types import DOMRectangle, InteractiveRegion

TOP_NO_LABEL_ZONE = 20  # Don't print any labels close the top of the page


def add_set_of_mark(
    screenshot: bytes | Image.Image | io.BufferedIOBase, ROIs: Dict[str, InteractiveRegion]
) -> Tuple[Image.Image, List[str], List[str], List[str]]:
    if isinstance(screenshot, Image.Image):
        return _add_set_of_mark(screenshot, ROIs)

    if isinstance(screenshot, bytes):
        screenshot = io.BytesIO(screenshot)

    # TODO: Not sure why this cast was needed, but by this point screenshot is a binary file-like object
    image = Image.open(cast(BinaryIO, screenshot))
    comp, visible_rects, rects_above, rects_below = _add_set_of_mark(image, ROIs)
    image.close()
    return comp, visible_rects, rects_above, rects_below


def _add_set_of_mark(
    screenshot: Image.Image, ROIs: Dict[str, InteractiveRegion]
) -> Tuple[Image.Image, List[str], List[str], List[str]]:
    visible_rects: List[str] = list()
    rects_above: List[str] = list()  # Scroll up to see
    rects_below: List[str] = list()  # Scroll down to see

    fnt = ImageFont.load_default(14)
    base = screenshot.convert("L").convert("RGBA")
    overlay = Image.new("RGBA", base.size)

    draw = ImageDraw.Draw(overlay)
    for r in ROIs:
        for rect in ROIs[r]["rects"]:
            # Empty rectangles
            if not rect:
                continue
            if rect["width"] * rect["height"] == 0:
                continue

            mid = ((rect["right"] + rect["left"]) / 2.0, (rect["top"] + rect["bottom"]) / 2.0)

            if 0 <= mid[0] and mid[0] < base.size[0]:
                if mid[1] < 0:
                    rects_above.append(r)
                elif mid[1] >= base.size[1]:
                    rects_below.append(r)
                else:
                    visible_rects.append(r)
                    _draw_r

*[truncated — see source for full prompt]*