# Run Application – Notepad

## Overview

This example demonstrates how to use **Power Automate for desktop** to launch a Windows application and open a text file.

The exercise uses Windows Notepad and the `sample.txt` file provided in the Chapter 3 `SampleData` folder.

It introduces a simple Desktop Flow and demonstrates how Power Automate for desktop can interact with a Windows application.

## Scenario

Suppose an automation needs to open a text file automatically for further processing.

Instead of manually opening Notepad and locating the file, a Desktop Flow can perform the following steps:

```text
Start Desktop Flow
       ↓
Launch Notepad
       ↓
Open sample.txt
       ↓
Display the file
