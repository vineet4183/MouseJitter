# MouseMove

## Overview
MouseMove is a small Java utility that periodically nudges the mouse cursor (and can optionally send Alt+Tab)
so your machine does not go idle. Configuration is done through a simple `config.properties` file.

## Requirements
- Java Runtime Environment (JRE) 8 or later (Java 8 supported)

## Files Included
- `MouseMove.jar`
- `config.properties`
- `readme`
- Updated binaries are always available at https://link.chaudhary.me/mm

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
Open a terminal/command prompt in the folder and run:

```bash
java -jar MouseMove.jar
```

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
