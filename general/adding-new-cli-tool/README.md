# Adding New Cli Tool

> ## Overview

This document describes the exact steps needed to add a new CLI tool to the cycod project ecosystem, based on how `cycodgr` was added.

#

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Adding a New CLI Tool to the Project

## Overview

This document describes the exact steps needed to add a new CLI tool to the cycod project ecosystem, based on how `cycodgr` was added.

## Reference Commit

The primary commit that added `cycodgr`: **14169d53** - "feat: Implement cycodgr - GitHub Repository and Code Search CLI (Phases A-E Complete)"

## Required Changes

### 1. Create Project Structure

```
src/<toolname>/
├── <toolname>.csproj          # Project file
├── Program.cs                 # Entry point
├── <ToolName>ProgramInfo.cs   # Program info class
├── README.md                  # Tool-specific documentation
├── CommandLine/               # Command-line parsing
│   ├── <ToolName>Command.cs
│   └── <ToolName>CommandLineOptions.cs
├── CommandLineCommands/       # Command implementations
│   └── <CommandName>Command.cs
├── Helpers/                   # Helper classes
│   └── <Feature>Helpers.cs
├── Models/                    # Data models (if needed)
│   ├── ModelA.cs
│   └── ModelB.cs
└── assets/                    # Embedded resources
    ├── help/                  # Help text files
    │   ├── usage.txt
    │   ├── examples.txt
    │   └── ...
    └── prompts/               # AI prompts (if needed)
        ├── system.md
        └── user.md
```

### 2. Create Project File (`<toolname>.csproj`)

**Key elements:**

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <!-- Import shared version settings -->
  <Import Project="../../BuildCommon.targets" />

  <PropertyGroup>
    <TargetFramework>net9.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
    <EnableDefaultCompileItems>true</EnableDefaultCompileItems>
    <AssemblyName>toolname</AssemblyName>
  
    <OutputType>Exe</OutputType>
    
    <!-- Cross-platform support -->
    <RuntimeIdentifiers>win-x64;linux-x64;osx-x64</RuntimeIdentifiers>
    
    <!-- NuGet Package Properties -->
    <PackageId>ToolName</PackageId>  <!-- PascalCase for NuGet -->
    <Authors>

*[truncated — see source for full prompt]*