
## Scenario

- My software isn't working and I need to debug it, but don't want to set up a debugger
- I don't want to modify my code to verify things are working as expected
- I want to know if something goes wrong when the code is running
- Deployed code is failing and there isn't a way to get a debugger attached

## Key Takeaways

- Use logging instead of built-in print functions
	- Allows for control of log levels to tune the output on demand

## Logging and printing output

- Can keep all the debugging printouts (just log them at a low DEBUG level)
- Configurable log levels allows for information to be available without changing code
- Consult with the project lead on how log levels are used in the project and how many there are

- Sometimes in a deployed system, if something goes wrong, logs may be the only breadcrumbs you have to figure out a problem. Make the messages clear!

## Log Levels

My take on log levels:

- DEBUG
	- all the info you would need to verify things are working or to find a problem
	- Will likely spam logs
- INFO
	- provides info about the high level operations that you may want to know about
	- Don't want these to spam the logs
- WARNING
	- When something wrong or unexpected happens, but you can recover
	- This is something you may want to know so you can look into and fix it later
- ERROR
	- Something bad happened and you can't recover from it

## Additional Resources

- [Python logging](https://docs.python.org/3/howto/logging.html)