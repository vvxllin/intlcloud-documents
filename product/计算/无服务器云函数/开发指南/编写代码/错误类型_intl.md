If an exception occurs during testing and executing a function, the SCF platform will handle the exception as much as possible and write the exception information to the log. Exceptions generated by function execution include caught exceptions (handled errors) and uncaught exceptions (unhandled errors). For example, you can explicitly throw an exception in the code:

```
def always_failed_handler(event,context):
    raise Exception('I failed!')
```

This function will throw an exception during execution and return the following error message:

```
File "/var/user/index.py", line 2, in always_failed_handler
raise Exception('I failed!')
Exception: I failed!
```
The SCF platform will record this error message in the function log.

If you need to test this snippet of code, please create a function and copy the function code above without adding any triggers. Click **Test** in the console and select the "Hello World" test sample to test.

You can define how to handle possible errors in your code to ensure the robustness and scalability of your application. For example, you can inherit the Exception class

```
class UserNameAlreadyExistsException(Exception): pass
            
def create_user(event):
    raise UserNameAlreadyExistsException('The username already exists,please change a name!')
```

Or, you can use the Try statement to catch errors:

```
def create_user(event):
    try:
        createUser(event[username],event[pwd])
    except UserNameAlreadyExistsException,e:
        //catch error and do something
```   
     
If no error catching is performed in your code logic, SCF will catch errors as much as possible. However, if an error that the platform cannot catch occurs, such as when your function suddenly crashes and exits during the execution process, the system will return a general error message.

The following table lists some common errors in code execution.

| Error scenario | Error message |
|--|--|
| raise is used to throw an exception |	{File "/var/user/index.py", line 2, in always_failed_handler raise Exception('xxx') Exception: xxx}|
| The handler does not exist | {'module' object has no attribute 'xxx'} |
| The dependency module does not exist | {global name 'xxx' is not defined} |
| Timed out | {"time out"} |
