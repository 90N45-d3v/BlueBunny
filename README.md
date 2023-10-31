![banner](https://github.com/90N45-d3v/BlueBunny/assets/79598596/1b5c3e5c-589e-4e9e-b72e-809aa072855c)
<p align="center">
 <img src="https://img.shields.io/badge/Made%20with-Python-blue">
 <img src="https://img.shields.io/github/license/90N45-d3v/BlueBunny.svg">
 <img src="https://img.shields.io/badge/Ask%20me-anything-1abc9c.svg">
 <br>
 <img src="https://img.shields.io/badge/-Linux-lightblue">
</p>
<p align="center">
  C2 solution that communicates directly over Bluetooth-Low-Energy with your Bash Bunny Mark II.<br>Send your Bash Bunny all the instructions it needs just over the air.
</p>

## Table of contents
- [Overview](https://github.com/90N45-d3v/BlueBunny#overview)
- [Installation & Start](https://github.com/90N45-d3v/BlueBunny#installation--start)
- [Manual communication with the Bash Bunny through Python](https://github.com/90N45-d3v/BlueBunny#manual-communication-with-the-bash-bunny-through-python)
- [Troubleshooting](https://github.com/90N45-d3v/BlueBunny#troubleshooting)
- [Working on...](https://github.com/90N45-d3v/BlueBunny#working-on)
- [Additional information](https://github.com/90N45-d3v/BlueBunny#additional-information)

## Overview
#### Structure
![BlueBunny-Structure](https://github.com/90N45-d3v/BlueBunny/assets/79598596/48498db0-87cb-4a46-8c58-63495bade5f3)


## Installation & Start
1. Install required dependencies
````
pip install pygatt "pygatt[GATTTOOL]"
````
2. Download BlueBunny's repository (and switch into the correct folder)
````
git clone https://github.com/90N45-d3v/BlueBunny
cd BlueBunny/C2
````
3. Start the C2 server
````
sudo python c2-server.py
````
4. Plug your Bash Bunny with the BlueBunny payload into the target machine (payload at: `BlueBunny/payload.txt`).
5. Visit your C2 server from your browser on `localhost:1472` and connect your Bash Bunny (Your Bash Bunny will light up green when it's ready to pair).


## Manual communication with the Bash Bunny through Python
You can use BlueBunny's BLE backend and communicate with your Bash Bunny manually.
#### Example Code
````python
# Import the backend (BlueBunny/C2/BunnyLE.py)
import BunnyLE

# Define the data to send
data = "QUACK STRING I love my Bash Bunny"
# Define the type of the data to send ("cmd" or "payload") (payload data will be temporary written to a file, to execute multiple commands like in a payload script file)
d_type = "cmd"

# Initialize BunnyLE
BunnyLE.init()

# Connect to your Bash Bunny
bb = BunnyLE.connect()

# Send the data and let it execute
BunnyLE.send(bb, data, d_type)
````

## Troubleshooting
#### Connecting your Bash Bunny doesn't work? Try the following instructions:
- Try connecting a few more times
- Check if your bluetooth adapter is available
- Restart the system your C2 server is running on
- Check if your Bash Bunny is running the BlueBunny payload properly
- How far away from your Bash Bunny are you? Is the environment (distance, interferences etc.) still sustainable for typical BLE connections?
#### Bugs within BlueZ
The Bluetooth stack used is well known, but also very buggy. If starting the connection with your Bash Bunny does not work, it is probably a temporary problem due to BlueZ. Here are some kind of errors that can be caused by temporary bugs. These usually disappear at the latest after rebooting the C2's operating system, so don't be surprised and calm down if they show up.
- Timeout after 5.0 seconds
- Unknown error while scanning for BLE devices

## Working on...
- Remote shell access
- BLE exfiltration channel
- Improved connecting process

## Additional information
As I said, BlueZ, the base for the bluetooth part used in BlueBunny, is somewhat bug prone. If you encounter any non-temporary bugs when connecting to Bash Bunny as well as any other bugs/difficulties in the whole BlueBunny project, you are always welcome to contact me. Be it a problem, an idea/solution or just a nice feedback.
