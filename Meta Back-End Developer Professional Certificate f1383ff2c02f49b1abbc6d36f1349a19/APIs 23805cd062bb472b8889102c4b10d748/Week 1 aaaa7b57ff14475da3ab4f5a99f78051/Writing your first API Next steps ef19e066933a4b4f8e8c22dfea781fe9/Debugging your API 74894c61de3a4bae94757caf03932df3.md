# Debugging your API

# What is debugging?

Debugging is the process of finding and fixing errors in your code. It helps you understand how your program works, and improves your code's efficiency. With debugging, you can quickly find the source of the issue, and solve it.

# Getting started with Debugging in Visual Studio Code

1. Open the terminal and activate the virtual environment for your project using pipenv shell.
2. Open the project in VS code, and select the Python interpreter from the command palette.
3. Create a new Django app and open it in VS code.
4. Find the debugger icon on the left sidebar, and click on it to open the debug panel.
5. Create a launch.json file by clicking the link at the top of the debug panel.
6. Select Django from the debug configuration list.

# Important terms related to debugging

1. Breakpoint: A position where you intentionally pause the execution of your code. You can examine the variables' values up to that point.
2. Watch: A list of variables that you monitor. You can examine their values whenever they change.

# The Debug Toolbar

1. Continue/Pause: Lets you execute code on the current line and continue until the next breakpoint is reached.
2. Step Over: Continues the execution to the next line and pauses.
3. Step Into: Goes to the function and pauses the code execution.
4. Step Out: Goes back to the line where it was called from inside a function.
5. Restart: Restarts the debugging session.
6. Stop: Ends the debugging session and stops the web server.

# Debugging in action

1. Open the views.py file in your app and add the code that is supposed to present some even numbers.
2. Create a route to access this function by browsing the numbers endpoint.
3. If nothing displays in the browser, it is an indication that there might be an error in the code.
4. Set a breakpoint on line 9, start the debugger, and revisit the endpoint.
5. If the debugger didn't pause code execution on line 9, it means that the value of the remainder was never set to zero.
6. Add the remainder variable to the watch list, set a new breakpoint on line 8, and restart the debugging session.
7. Step over a few more times and examine the remainder's value.
8. If the remainder should be either 0 or 1, examine line 7 closely.
9. If the division operator was used instead of the modulo, fix the code and replace the division operator with modulo.
10. Remove all the breakpoints, restart the debugging session, and revisit the endpoint.

# Conclusion

In this video, you learned about debugging and how it works in Visual Studio Code. You also learned about important terms such as breakpoints and watch, and how to use the debug toolbar. With this knowledge, you'll be able to quickly find and fix errors in your code in all of your future API projects.