# Validator

> +++
date = "2016-04-28T23:45:48+01:00"
title = "Project 6: Validator"
+++


A validation tool for excel files. Sometimes you need to export data from 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
+++
date = "2016-04-28T23:45:48+01:00"
title = "Project 6: Validator"
+++


A validation tool for excel files. Sometimes you need to export data from one system for loading into another. For instance
you may export a report from a derivatives trading system for information for a collateral management system.

This Excel macro file validates input files to make sure that they are in a specific format.
The input file can be in any format that excel can load. The workbook will load the file and check for errors in place.

<!--more-->



The workbook is configurable so it can be used to validate any input.

The workbook currently supports the following validation.

1. It can validate that the correct columns are in the input file.
2. It can validate columns in the file to make sure that they are in the correct date and number format.
3. It can validate that the columns in the file are in a selection list it does this by using a map tab with tables.
4. It can validate that the contents in the columns do not exceed a specific length.
5. It can validate that when a column is required it contains data.


It will show the error count after it has completed running and will highlight which cells in the input failed the validation.

![](img/validator.png)


So I will just go through some of the functionality

## Step 1: load the input for processing

The first part is we load the input file for processing

This function loads any valid excel file into the workbook, it will load it into a named tab.
Notice how I delete and recreate the tab at the beginning of the process.
The remove sheet function should just fail silently as the sheet may not exist for deletion.

```vb

Function loadFile(path As String, name As String)
    Dim ws As Worksheet
    Set ws = addSheet(name)
    Dim wbFrom As Workbook
    Set wbFrom = Workbooks.Open(path)
    wbFrom.Sheets(1).Cells.Copy ws.Cells
    wbFrom.Close SaveChanges:=False
    Set loadFile = ws
End Function

Function addSheet(name As String

*[truncated — see source for full prompt]*