# printer-movement-generator
Script to generate random movement commands for testing 3D printers.
# Start and stop G-code
The code includes a vary basic start and end gcode, it should work fine on most printers, but **always** check the code for your exact requirements! 
If needed you can change the start and end code on the top of the `create-gcode.py` script.
# Usage
Generate random 3D printer movements (G1) into test.gcode 
Use the provided CLI options in the table below to customize your test run.

### CLI options

| Option | Type | Required | Description | Example |
|:---:|:---:|:---:|:---:|:---:|
| -h, --help | flag | ❌ | Show help and exit | -h |
| --min-x | float | ✅ | Minimum X coordinate | --min-x 0 |
| --max-x | float | ✅ | Maximum X coordinate | --max-x 200 |
| --min-y | float | ✅ | Minimum Y coordinate | --min-y 0 |
| --max-y | float | ✅ | Maximum Y coordinate | --max-y 200 |
| --min-z | float | ❌ | Minimum Z coordinate (optional; must supply with --max-z) | --min-z 0.2 |
| --max-z | float | ❌ | Maximum Z coordinate (optional; must supply with --min-z) | --max-z 10 |
| --feedrate | float | ✅ | Feedrate in mm/s (converted to mm/min in G-code) | --feedrate 5000 |
| --count | int | ✅ | Number of movement commands to generate | --count 200 |
| -p MS, --pause MS | int (ms) | ❌ | Pause after each move in milliseconds (inserts `G4 P<ms>` after each G1) | -p 100 |