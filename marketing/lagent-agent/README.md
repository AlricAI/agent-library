# Lagent Agent

> import copy
import json
from typing import Any, Iterator, List, Union

import requests
from lagent.actions import ActionExecutor
from lagent.agents im

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import copy
import json
from typing import Any, Iterator, List, Union

import requests
from lagent.actions import ActionExecutor
from lagent.agents import internlm2_agent
from lagent.llms.base_llm import BaseModel
from lagent.llms.meta_template import INTERNLM2_META
from lagent.schema import AgentStatusCode, ModelStatusCode
from lagent.utils.util import filter_suffix

from .. import message_schema as msg
from ..logging import logger
from ..ui import get_translator
from ..utils import parse_inputs

i18n = get_translator(__file__)


class LMDeployClient(BaseModel):
    """An LMDeploy client without lmdeploy dependency."""
    def __init__(self, url: str, model_name: str, **kwargs):
        BaseModel.__init__(self, path=url, **kwargs)
        self.completions_v1_url = f'{url}/v1/completions'
        self.model_name = model_name

    def stream_chat(self,
                    inputs: List[dict],
                    session_id=0,
                    sequence_start: bool = True,
                    sequence_end: bool = True,
                    ignore_eos: bool = False,
                    timeout: int = 30,
                    **kwargs):
        gen_params = self.update_gen_params(**kwargs)
        prompt = self.template_parser(inputs)

        resp = ''
        finished = False
        stop_words = self.gen_params.get('stop_words')
        for text in self.stream_completions(
                model=self.model_name,
                prompt=prompt,
                session_id=session_id,
                sequence_start=sequence_start,
                sequence_end=sequence_end,
                ignore_eos=ignore_eos,
                timeout=timeout,
                **gen_params):
            resp += text['choices'][0]['text']
            if not resp:
                continue
            # remove stop_words
            for sw in stop_words:
                if sw in resp:
                    resp = filter_suffix(resp, stop_words)
                    finished = True
               

*[truncated — see source for full prompt]*