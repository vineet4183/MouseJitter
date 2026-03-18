# MouseMove

## Overview
MouseMove is a small Java utility that periodically moves the mouse cursor (and can optionally send Alt+Tab)
so your machine does not go idle. Configuration is done through a simple `config.properties` file.

Official website: https://mm.chaudhary.me

## What You Can Achieve
MouseMove is designed to help you maintain an active presence on your system automatically:
- **Avoid Screensavers**: Prevent screensavers from triggering with periodic mouse movements
- **Keep MS Teams Active**: Maintain active status in Microsoft Teams so colleagues see you as online
- **Combat Idle Detection**: Work around idle timeout policies that might lock your screen or disconnect sessions
- **Custom Scheduling**: Run the utility only during specific hours (e.g., 9 AM - 5:30 PM) or specific days
- **Flexible Movement Options**: Choose between random cursor movements or consistent offsets in horizontal, vertical, or both directions
- **Optional Alt+Tab Integration**: Optionally send Alt+Tab keystrokes to switch windows and further prevent idle detection

## Safety & Security
This utility is **completely safe to use** with the following guarantees:
- **No Malware**: The utility will NOT be detected or flagged by any anti-malware, anti-virus, or endpoint detection software
- **No Admin Rights Required**: Can be run without administrator privileges, making it suitable for corporate environments
- **Lightweight**: Uses minimal system resources with virtually no performance impact
- **No Network Access**: The utility operates entirely locally—it does not phone home or transmit data
- **Legal Use**: Designed for personal use cases where you need to prevent idle detection (not for circumventing security policies maliciously)
- **Fully Controllable**: You have complete control over when it runs, what it does, and can stop it at any time

## Requirements
- Java Runtime Environment (JRE) 8 or later (Java 8 supported)

## Files Included
- `MouseMove.jar`
- `config.properties`
- `README.md`

## Install / Setup
1. Install Java 8 or later.
2. Place `MouseMove.jar` and `config.properties` in the same folder.
3. Edit `config.properties` to match your schedule and preferences.

## No-Admin Java Setup (Portable JRE)
If you don't have admin rights, you can use a standalone/portable JRE zip:
1. Download a JRE 8+ standalone zip from a vendor that provides ZIP archives.
   Oracle JRE download page:
   - https://www.oracle.com/java/technologies/downloads/
2. Extract the zip to a folder you can write to, e.g. `C:\Tools\jre8` or `D:\Apps\Java\jre`.
3. Set environment variables to use this JRE:
   - Set `JAVA_HOME` to the extracted folder (e.g. `C:\Tools\jre8`)
   - Add `%JAVA_HOME%\bin` to your `PATH`
4. Open a new terminal and verify:

   ```bash
   java -version
   ```

   It should show Java 8 or later.

## Run

### Step-by-Step Instructions Using Command Prompt (cmd)

#### Option 1: Using File Explorer
1. **Open File Explorer** and navigate to the folder containing `MouseMove.jar` and `config.properties`
2. **Open Command Prompt in this folder**:
   - On Windows 10/11: Click the address bar at the top, type `cmd`, and press Enter
   - Alternative: Hold `Shift` + Right-click in the folder (empty space), select "Open command window here" or "Open PowerShell window here"
3. In the command prompt window, type the following command and press Enter:
   ```cmd
   java -jar MouseMove.jar
   ```
4. You should see the application start and display status messages

#### Option 2: Using Windows Run Dialog (Fastest)
1. **Press `Win + R`** to open the Run dialog
2. Type the full command below (replace the path with your actual folder location):
   ```cmd
   cmd /k cd /d "C:\Path\To\MouseMove\Folder" && java -jar MouseMove.jar
   ```
   For example:
   ```cmd
   cmd /k cd /d "C:\Users\YourName\Desktop\MouseMove" && java -jar MouseMove.jar
   ```
3. Press Enter

#### Option 3: From Any Location Using Command Prompt
1. **Press `Win + R`** and type `cmd` then press Enter
2. In the command prompt, navigate to your MouseMove folder:
   ```cmd
   cd C:\Path\To\MouseMove\Folder
   ```
   For example:
   ```cmd
   cd C:\Users\YourName\Desktop\MouseMove
   ```
3. Then run:
   ```cmd
   java -jar MouseMove.jar
   ```

### What to Expect
- The application will start and begin running in the command prompt window
- You'll see log messages indicating when mouse movements occur
- The application will stop when `EndTime` is reached (based on your `config.properties` settings)
- To stop the application at any time, press `Ctrl + C` in the command prompt window

## Configuration
The app reads `config.properties` from the same folder as the jar (this overrides the built-in defaults).

Key options:
- `interval` = seconds between moves (required, > 0)
- `movetype` = `random` | `offset`
- `offset` = pixels to move when `movetype=offset`
- `direction` = `horizontal` | `vertical` | `both`
- `alttab` = `true` | `false`
- `altTabInterval` = send Alt+Tab every N moves (when `alttab=true`)
- `StartTime` = `HHmm` or `HH:mm` (24-hour local time)
- `EndTime` = `HHmm` or `HH:mm` (24-hour local time)
- `numOfDays` = `0` to run indefinitely, or `N` to stop after N days at `EndTime`
- `Monday`..`Sunday` = `true` | `false` (case-insensitive keys)

Example config:

```properties
interval=30
movetype=offset
offset=100
direction=both
alttab=true
altTabInterval=5
StartTime=0900
EndTime=1730
numOfDays=1
Monday=true
Tuesday=true
Wednesday=true
Thursday=true
Friday=true
Saturday=false
Sunday=false
```

## Notes
- The app only runs during enabled days and between `StartTime` and `EndTime`.
- If `EndTime` is earlier than `StartTime`, the window crosses midnight.
- Logs display time in 12-hour format with date in `dd-MMM-yyyy`.
