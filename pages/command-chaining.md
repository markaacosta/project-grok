# Command Chaining

Multiple shell commands can be written and executed together, like so:

`echo "starting..."; sleep 3; echo "finishing..."`

this command prints "starting", waits 3 seconds, then prints "finishing"; if any command *fails*, the next command will still be executed. Sometimes this is not desirable; we may only want some command to execute if the prior command(s) did first and were *successful*. To accomplish this, replace semicolons with `AND` operators...

`echo "starting..." && sleep 3 && echo "finishing..."`

![chaining](../assets/chaining.gif)