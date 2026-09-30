# Windows Utilman Privilege Escalation (PoC)

## Overview
This laboratory project demonstrates how offline access to a Windows system can be leveraged to bypass local authentication via the Utility Manager (`Utilman.exe`). By replacing `Utilman.exe` with `cmd.exe` through the Windows Recovery Environment (WinRE), an administrator or tester can launch an elevated Command Prompt with `SYSTEM` privileges directly from the lock screen.

---

## Lab Environment & Tools
* **OS:** Windows 11
* **Environment:** Windows Recovery Environment (WinRE)
* **Target Binary:** `C:\Windows\System32\Utilman.exe`
* **Tools Used:** Command Prompt (`cmd.exe`), User Accounts Manager (`netplwiz`)

---

## Step-by-Step Proof of Concept (PoC)

### 1. Accessing Recovery Environment
Booted the machine into the Windows Recovery Environment (WinRE) to access a command prompt without entering the active Windows desktop environment.

### 2. File Modification in System32
Navigated to `C:\Windows\System32` and executed the following commands to back up the original Utility Manager binary and swap it with Command Prompt:
```cmd
ren utilman.exe utilman.bak
copy cmd.exe utilman.exe


