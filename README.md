# printer-movement-generator
Script to generate random movement commands for testing 3D printers.
# Usage
Example for a Voron 2.4 350x350 printer: `python .\create-gcode.py --min-x 50 --max-x 300 --min-y 50 --max-y 300 --feedrate 300 --count 300python .\create-gcode.py --min-x 50 --max-x 300 --min-y 50 --max-y 300 --feedrate 300 --count 300`
Generate random 3D printer movements (G1) into test.gcode. 
Use the provided CLI options in the table below to customize your test run. 
 
- The Z ccordinates are optional, if you want to generate randomness in the Z direction too, you need to specify a minimum and maximum Z.
- If you only want to use the XY plane, then there won't be any Z coordinates included in the gcode. This means that, the printer will move at Z=100 (if you don't change the default `PRINT_START`).
- If you want to set another Z height, you need to edit the `PRINT_START` or add some commands manually.
## Start and stop G-code
The code includes a vary basic start and end gcode, it should work fine on most printers, but **always** check the code for your exact requirements! 
If needed, you can change the start and end code on the top of the `create-gcode.py` script.
### CLI options

| Option | Type | Required | Description | Example |
|:---:|:---:|:---:|:---:|:---:|
| -h, --help | flag | ❌ | Show help and exit | -h |
| --min-x | float | ❌ | Minimum X coordinate (default: 10) | --min-x 0 |
| --max-x | float | ✅ | Maximum X coordinate | --max-x 200 |
| --min-y | float | ❌ | Minimum Y coordinate (default: 10) | --min-y 0 |
| --max-y | float | ✅ | Maximum Y coordinate | --max-y 200 |
| --min-z | float | ❌ | Minimum Z coordinate (optional; must supply with --max-z) | --min-z 0.2 |
| --max-z | float | ❌ | Maximum Z coordinate (optional; must supply with --min-z) | --max-z 10 |
| --feedrate | float | ✅ | Feedrate in mm/s (converted to mm/min in G-code) | --feedrate 5000 |
| --count | int | ✅ | Number of movement commands to generate | --count 200 |
| -p MS, --pause MS | int (ms) | ❌ | Pause after each move in milliseconds (inserts `G4 P<ms>` after each G1) | -p 100 |