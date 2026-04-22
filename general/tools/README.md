# Tools

> """
CrewAI tool wrappers for Java Analyzer Agent
"""

import json
import os
import zipfile
from pathlib import Path
from typing import Dict, List, Uni

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
CrewAI tool wrappers for Java Analyzer Agent
"""

import json
import os
import zipfile
from pathlib import Path
from typing import Dict, List, Union

from crewai.tools import tool
from utils.logging_config import get_agent_logger

logger = get_agent_logger("java_analyzer.tools")


class JavaAnalyzerTools:
    """Collection of CrewAI tools for Java mod analysis"""

    def __init__(self, agent_instance=None):
        self.agent_instance = agent_instance

    @tool
    @staticmethod
    def analyze_mod_structure_tool(mod_data: Union[str, Dict]) -> str:
        """
        Analyze the overall structure of a Java mod.

        Args:
            mod_data: JSON string containing mod file path and analysis options

        Returns:
            JSON string with structural analysis results
        """
        from agents.java_analyzer import JavaAnalyzerAgent

        agent = JavaAnalyzerAgent.get_instance()

        def _determine_mod_type_and_framework(mod_path: str) -> Dict[str, str]:
            """Determine mod type and framework"""
            if mod_path.endswith((".jar", ".zip")):
                mod_type = "jar"
                with zipfile.ZipFile(mod_path, "r") as jar:
                    file_list = jar.namelist()
                    framework = agent._detect_framework_from_jar_files(file_list, jar)
            elif os.path.isdir(mod_path):
                mod_type = "source"
                framework = agent.framework_indicators.get("unknown", "unknown")
            else:
                mod_type = "unknown"
                framework = "unknown"

            return {"type": mod_type, "framework": framework}

        def _analyze_jar_structure(jar_path: str, analysis_depth: str) -> Dict:
            """Analyze JAR file structure"""
            structure = {
                "total_files": 0,
                "package_structure": {},
                "main_classes": [],
                "resource_files": [],
                "metadata_files": [],
            }

   

*[truncated — see source for full prompt]*