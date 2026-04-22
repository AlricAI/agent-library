# Packaging Agent

> """
Packaging Agent for assembling converted components into .mcaddon packages
"""

from typing import Dict, List, Any

import logging
import json
imp

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Packaging Agent for assembling converted components into .mcaddon packages
"""

from typing import Dict, List, Any

import logging
import json
import zipfile
import os
import copy
from pathlib import Path
import uuid
from crewai.tools import tool
from models.smart_assumptions import SmartAssumptionEngine
from agents.bedrock_manifest_generator import BedrockManifestGenerator
from agents.block_item_generator import BlockItemGenerator
from agents.entity_converter import EntityConverter
from agents.file_packager import FilePackager
from agents.addon_validator import AddonValidator
from agents.packaging_validator import PackagingValidator

logger = logging.getLogger(__name__)


class PackagingAgent:
    """
    Packaging Agent responsible for assembling converted components into
    .mcaddon packages as specified in PRD Feature 2.
    """

    _instance = None

    def __init__(self):
        self.smart_assumption_engine = SmartAssumptionEngine()

        # Initialize enhanced Bedrock generation components
        self.manifest_generator = BedrockManifestGenerator()
        self.block_item_generator = BlockItemGenerator()
        self.entity_converter = EntityConverter()
        self.file_packager = FilePackager()
        self.addon_validator = AddonValidator()
        self.packaging_validator = PackagingValidator()

        # Bedrock package structure templates
        self.manifest_template = {
            "format_version": 2,
            "header": {
                "name": "",
                "description": "",
                "uuid": "",
                "version": [1, 0, 0],
                "min_engine_version": [1, 19, 0],
            },
            "modules": [],
        }

        # Required directories for different pack types
        self.pack_structures = {
            "behavior_pack": {
                "required": {"manifest.json": "manifest"},
                "optional": {
                    "pack_icon.png": "icon",
                    "scripts/": "scrip

*[truncated — see source for full prompt]*