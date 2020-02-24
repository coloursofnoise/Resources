# Getting Input
## Input Class

Celeste uses the `static Input` class to retrieve user input when needed. The Input class contains a number of members, each referencing a different input.

Luckily, getting input from within your own code mod is as simple as getting the value held within the field you need.
Ex: `Input.Jump.Pressed`

Most values are pretty self-evident, such as the state of a button or key, represented as a boolean, but some require a little more explanation.

### Buttons
Each button has a few relevant values: Pressed, Released, and Check. These return the following:
- Check - Is the button currently pressed?
- Pressed - Was the button just pressed?
- Released - Was the button just released?

### Axis Movement
Axis movement is split into the `MoveX` and `MoveY` fields, as well as `GliderMoveY` for Jellies(?)

Each Axis returns a floating point value between -1 and 1.

### Joystick
Joystick position, under the `Aim` member, is used primarily for movement while in a Feather. (there is also MountainAim, but idk what that’s for)

The Aim value is an `Xna.Framework Vector2` with both values clamped between -1 and 1.

#Creating a New Input
To Be Added

For questions and feedback, please contact @coloursofnoise on the Celeste [Discord](https://discord.gg/6qjaePQ).

