# Base

> #
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtai

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Copyright 2025 Dimensional Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

from abc import ABC, abstractmethod
import logging
from dimos.exceptions.agent_memory_exceptions import UnknownConnectionTypeError, AgentMemoryConnectionError
from dimos.utils.logging_config import setup_logger

# TODO
# class AbstractAgentMemory(ABC):

# TODO
# class AbstractAgentSymbolicMemory(AbstractAgentMemory):

class AbstractAgentSemanticMemory(): # AbstractAgentMemory):
    def __init__(self, connection_type='local', **kwargs):
        """
        Initialize with dynamic connection parameters.
        Args:
            connection_type (str): 'local' for a local database, 'remote' for a remote connection.
        Raises:
            UnknownConnectionTypeError: If an unrecognized connection type is specified.
            AgentMemoryConnectionError: If initializing the database connection fails.
        """
        self.logger = setup_logger(self.__class__.__name__)
        self.logger.info('Initializing AgentMemory with connection type: %s', connection_type)
        self.connection_params = kwargs
        self.db_connection = None  # Holds the conection, whether local or remote, to the database used.
        
        if connection_type not in ['local', 'remote']:
            error = UnknownConnectionTypeError(f"Invalid connection_type {connection_type}. Expected 'local' or 'remote'.")
            self.logger.error(str(error))
            raise error

        try:
            if connection_t

*[truncated — see source for full prompt]*