# Framework Detector

> """
Framework detection for Forge/Fabric/Quilt mods
"""

import zipfile

from utils.logging_config import get_agent_logger

logger = get_agent_logger(

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Framework detection for Forge/Fabric/Quilt mods
"""

import zipfile

from utils.logging_config import get_agent_logger

logger = get_agent_logger("java_analyzer.framework_detector")


class FrameworkDetector:
    """Detects modding framework (Forge/Fabric/Quilt/etc) from JAR contents"""

    FRAMEWORK_INDICATORS = {
        "forge": ["net.minecraftforge", "cpw.mods", "@Mod", "ForgeModContainer"],
        "fabric": ["net.fabricmc", "FabricLoader", "fabric.mod.json"],
        "quilt": ["org.quiltmc", "QuiltLoader", "quilt.mod.json"],
        "bukkit": ["org.bukkit", "plugin.yml", "JavaPlugin"],
        "spigot": ["org.spigotmc", "SpigotAPI"],
        "paper": ["io.papermc", "PaperAPI"],
    }

    def detect_framework_from_jar(self, jar_path: str) -> str:
        """Detect modding framework from JAR file contents"""
        try:
            with zipfile.ZipFile(jar_path, "r") as jar:
                file_list = jar.namelist()
                return self._detect_framework_from_files(file_list, jar)
        except Exception as e:
            logger.warning(f"Error detecting framework: {e}")
            return "unknown"

    def _detect_framework_from_files(self, file_list: list, jar: zipfile.ZipFile) -> str:
        """Detect framework from file list and optionally file contents"""
        for framework, indicators in self.FRAMEWORK_INDICATORS.items():
            for indicator in indicators:
                if any(indicator in file_name for file_name in file_list):
                    return framework

        for file_name in file_list:
            if file_name.endswith(".json") and "mod" in file_name.lower():
                try:
                    content = jar.read(file_name).decode("utf-8")
                    for framework, indicators in self.FRAMEWORK_INDICATORS.items():
                        for indicator in indicators:
                            if indicator in content:
                                return framework
                except (UnicodeDec

*[truncated — see source for full prompt]*