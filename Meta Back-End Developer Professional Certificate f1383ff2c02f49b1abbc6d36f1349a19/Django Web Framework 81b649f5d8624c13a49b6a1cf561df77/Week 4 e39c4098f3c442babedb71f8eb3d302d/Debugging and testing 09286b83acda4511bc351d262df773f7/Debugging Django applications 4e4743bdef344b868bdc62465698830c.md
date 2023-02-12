# Debugging Django applications

# Introduction

- Debugging is an important part of the development process that helps identify, isolate, and solve errors in a web framework, such as Django.
- Debugging can be challenging in Django, as web projects often consist of interlinked files and dependencies that make it difficult to troubleshoot. However, debugging can help you build a better understanding of the internal workings of an application.
    
    ![Screenshot 2023-01-29 at 10.57.46 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_10.57.46_AM.png)
    

![Screenshot 2023-01-29 at 10.58.08 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_10.58.08_AM.png)

# Debugging in Django

- Django has its own debugger, which appears as a yellow page error and is enabled by default.
- The settings for the debugger can be found and modified in the settings.py file of your project. **However, the developers of Django recommend that the debugger should never be used in the production environment**, as it may expose internal file parts, database, and project configuration details to the end user. You can prevent this by setting the debug flag to false.
- In addition to the default debugger, Django can easily integrate third-party libraries to help with debugging. Here are a few ways to debug Django applications:
    
    ![Screenshot 2023-01-29 at 10.58.29 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_10.58.29_AM.png)
    

![Screenshot 2023-01-29 at 10.58.47 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_10.58.47_AM.png)

# Debugging Python code

Python specific errors will most likely appear in the console log. 

For example, if you comment out the **`shifts`** constant and save the file, you will get an error log in the console that says **`name 'shifts' is not defined`**. If you try to refresh the localhost URL in the browser, the page will not load.

![Screenshot 2023-01-29 at 10.59.34 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_10.59.34_AM.png)

# Debugging in Django Code

Yellow page errors in Django are more specific to problems within Django rather than Python code. For example, if you remove the CSRF token code from the file **`mytemplatehome.html`**
 and save the file, you will get an error that says **`Forbidden (CSRF verification failed)`**
 when you submit the form.

![Screenshot 2023-01-29 at 11.00.05 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_11.00.05_AM.png)

![Screenshot 2023-01-29 at 11.00.23 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_11.00.23_AM.png)

# Debugging Templates

If you misconfigure the template you are trying to render, you will get an error such as **`TemplateDoesNotExist`**. 

The traceback stack will contain the Python code in sequential order, with a specific line highlighted that is likely the source of the error. You can switch to a cleaner interface that displays all the details, and even share the traceback on a public website for further help.

![Screenshot 2023-01-29 at 11.00.57 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_11.00.57_AM.png)

![Screenshot 2023-01-29 at 11.01.06 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_11.01.06_AM.png)

![Screenshot 2023-01-29 at 11.01.19 AM.png](Debugging%20Django%20applications%204e4743bdef344b868bdc62465698830c/Screenshot_2023-01-29_at_11.01.19_AM.png)

# Conclusion

Debugging in Django takes patience and a systematic approach, but with practice, the number of errors you encounter will decrease. In this video, you learned how to debug Django applications, which will help you troubleshoot errors in the future.