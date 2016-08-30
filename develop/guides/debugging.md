# Testing and Debugging Roku Channels

![](../../images/debugger-console.png)

### Overview

Testing Roku Channels involves using a debug console and access to a variety of ports. The debug console provides a window into the runtime environment and provides features such as crash logs, stack-traces and much more.

**Sections:**

* [Accessing the debug console](#accessing-the-debug-console)
* [Debug ports](#debug-ports)
* [BrightScript debug console commands](#brightscript-debug-console-port-8085-commands)
* [SceneGraph debug ports](#scenegraph-debug-ports)
* [SceneGraph debug server commands](#scenegraph-debug-server-port-8080-commands)
* [r2d2 debugging]

---

## Accessing the debug console

The [Roku Plugin for Eclipse](/develop/developer-tools/eclipse-plugin.md) contains a built-in console with access to all the available debug ports.

The debug console can also be accessed using telnet through a shell application such as [PuTTY](http://www.putty.org/) for Windows or terminal on Mac and Linux: `telnet roku-ip-adress 8085`

The console shows the output of your channel during run time. If the channel crashes, the debugger will display the line number of the error, as well as the contents of variables at the time of the crash. If there is a syntax error in the code, it will also be described here. The developer console should be open whenever a channel is side-loaded to catch any possible startup errors.

In addition to displaying console output, the shell can also be used as an interactive debugger. When your application is running, simply press `ctrl + c` to break the application and enter debug mode. You will see the BrightScript Debugger prompt where you can type in commands.

> :information_source: You can also force your channel to break at a specific point by adding the `stop` command anywhere in your code.

## Debug ports

| Port    | Thread    | Description        |
| ------- | --------- | ------------------ |
| 8080    | debug server | debug server containing a host of utilities
| 8085    | Main()    | BrightScript runtime environment
| 8087    | Screensavers | The starting point for screensavers.

## BrightScript debug console (port 8085) commands

| Command | Description |
| ------- | ----------- |
| `bsc`	    | Print current BrightScript Component instances
| `bscs`    |	Print a summary of BrightScript component instance counts by component type.
| `brkd`	  | Toggle whether BrightScript should break into the debugger after non-fatal diagnostic messages.
| `bt`	    | Print backtrace of call function context frames
| `classes`	| Print Brightscript Component classes
| `cont` or `c`	| Continue Script Execution
| `down` or `d`	| Move down the function context chain one
| `exit`	  | Exit shell
| `gc`	    | Run garbage collector
| `help`	  | Print the list of debugger commands
| `last`	  | Print the last line that executed
| `list`	  | List current function
| `next`	  | Print the next line to execute
| `print`, `p`, or `?`	| Print a variable or expression
| `step`, `s`, or `t`	| Step one program statement
| `over`	  | Step over function (_Available since firmware version 7.2_)
| `out`	    | Step out of a function (_Available since firmware version 7.2_)
| `up` or `u`	| Move up the function context chain one
| `var`	    | Print local variables and their types/values

> :information_source: BrightScript statements can also be compiled and execute in the console. This can be used to change variables during execution or call a function that prints useful information about the state of your program.

## SceneGraph applications

SceneGraph applications can be debugged using the same tools as previous Roku applications. However, there are some additional ports that can be used to debug specific threads of SceneGraph applications, and port 8085 has limited value in debugging SceneGraph applications.

## SceneGraph debug ports

Because SceneGraph applications run on their own thread, and can also launch additional asynchronous threads using a Task node, five additional ports are available for debugging, as follows.

| Port    | Thread    | Description        |
| ------- | --------- | ------------------ |
| 8085    | Main()    | For SceneGraph applications, the Main() function only starts the SceneGraph application thread, so provides no debugging information about the SceneGraph application itself.
| 8089    | SceneGraph| The main SceneGraph application thread. This contains all of the debugging information for SceneGraph applications, except for information returned from asynchronous threads launched by a Task node.
| 8090    | First Task node thread | The first asynchronous thread launched by a Task node. If only one asynchronous thread is running after the Task node thread is launched, this port will show the debugging information for that thread.
| 8091    | Second Task node thread | The second asynchronous thread launched by a Task node. If there are two asynchronous threads running after a Task node is launched, this port will show the debugging information for the second thread launched.
| 8092    | Third Task node thread | The third asynchronous thread launched by a Task node. If there are three asynchronous threads running after a Task node is launched, this port will show the debugging information for the third thread launched.
| 8093    | More than three task node threads | This port is used if there are more than three asynchronous threads that have been launched by a Task node. If there are more than three asynchronous threads running after a Task node is launched, this port will show all the debugging information for all the threads launched after the third asynchronous thread.

### SceneGraph debug server (port 8080) commands
| Command | Description |
| ------- | ----------- |
| `sgnodes all` | Prints every existing node created by the currently running channel
| `sgnodes roots` | Prints every existing node without a parent created by the currently running channel. The existence of these unparented nodes means they are being kept alive by direct BrightScript references. These could be in variables local to a function, arrays, or associative arrays, including a component global `m` or an associative array field of a node.
| `sgnodes node_ID` | Prints nodes with an id field set to node_ID, except it bypasses all the hierarchy and rules, and just runs straight down the whole list in the order of node creation. It will list multiple nodes if there are several that match.
| `r2d2_bitmaps` | Prints a list of assets loaded into texture memory and the amount of free, used, and maximum available memory on your device, respectively. | 

> :information_source: These commands are similar to the getAll() , getRoots() ,  getRootsMeta(), and getAllMeta() [ifSGNodeChildren](https://sdkdocs.roku.com/display/sdkdoc/ifSGNodeChildren) methods, which can be called on any SceneGraph node.
