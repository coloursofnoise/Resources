For anyone with installation issues with Ahorn, please post your error logs in #modding_help, preferably the file or via a pasting service such as [https://hatebin.com/](https://hatebin.com/), and wait for help.
The error log is located at `%localappdata%/Ahorn/error.log` on Windows and `~/.config/Ahorn/error.log` on Linux and Mac
If you feel confident in your own ability to identify and resolve the issue, here are some common issues, and the potential solution to them.

# The following terms will be used in the cases below
* NSIS installer - The .exe installer file for Windows, comming with standalone Julia
* Cross platform installer - The instructions on the Github website, system installed Julia ran with `julia install_ahorn.jl`
* Julia REPL - The Julia REPL, "terminal", "black box". Allows running arbitrary Julia code easily.
* Opening the Julia REPL - In this case will also include activating the Ahorn environment, guide below.
* PATH - The system environment variable PATH, this is where programs are searched for by the command line.

# How to open the Julia REPL and activate the Ahorn environment
### With NSIS
> Assumes default install location
> 
> Open the REPL by navigating to `%localappdata%/CelestialCartographers/Ahorn/julia.bat`
> 
> The correct environment will already be set by this, and you are ready to go

### With Crossplatform
> Open Julia normally
> 
> Run the following code
> 
> On windows: `using Pkg; Pkg.activate(ENV["LocalAppData"] * "/Ahorn/env")`
> 
> On Linux/Mac: `using Pkg; Pkg.activate(ENV["HOME"] * "/.config/Ahorn/env")`

# Common cases
Work in progress! Your problem might not be here (yet)!
If your problem is not listed below, make sure to check the pinned messages in `#map_making`, `#modding_help`, and `#modding_welcome` for potential fixes.

## `julia is not a recognized as an internal or external command` (or equivalent for Linux/Mac)
This means that you do not have `julia` in your PATH.
You can either add Julia to your path variable, or substitute it for the whole path.
On Windows, using Julia 1.2.0 that would be `%localappdata%\Julia-1.2.0\bin\julia.exe`
For example installing Ahorn like that would be `%localappdata%\Julia-1.2.0\bin\julia.exe install_ahorn.jl`, assuming install_ahorn.jl is in the working directory.

## I installed Ahorn, but how do I run it?
### With NSIS:
* The installer should have created a shortcut for you, either in the programs list or as a shortcut on the desktop. 
* If this is not the case, you can run `%localappdata%/CelestialCartographers/Ahorn/ahorn.bat`

### With Crossplatform:
* On Linux and Mac the installer should have created `ahorn.sh` in the current directory you ran `julia install_ahorn.jl` in. Simply run this through the terminal.
* On Windows you will have to download Ahorn.bat from the Github repository
## Press any key to continue when starting Ahorn
This means a error has occured, check the error log.

## Ahorn doesn't start, but it doesn't give the message above
The first start is quite slow, give it some time. Make sure you have not frozen execution in the terminal (done by clicking in it on Windows).

## Error with `could not load library "libgobject-2.0-0"`
Gtk failed to build, and has to be rebuilt.
This can be attempted (and still has a chance to fail, I'm not sure why exactly it is a issue) by rebuilding it via the Julia REPL.
Potential solution:
> Open the REPL
> 
> Run the following code
> 
> `using Pkg; Pkg.build("Gtk")`
> 
> Any errors should be visible in the terminal afterwards. If it outputs "false", or simply nothing at all (besides the progress graphs), the problem should be resolved.

In some cases it will fail again to build GTK, I have no idea why, but attempting multiple rebuilds has worked for some. Just make sure to keep an eye on the REPL/errorlog to see that it is the same issue.

## Error with `checkpoints0.data`
This file was moved with the Farewell update to Celeste, causing older versions of Ahorn to crash since it is missing.
The easiest solution for this is to simply update Ahorn from the Julia REPL.
> Open the REPL
> 
> Run the following code
> 
> `using Pkg; Pkg.update()`
If no errors occurs, then you are done. 