# Windows Remote Server Library

## Methods
### run(cmd:_str_, capture_error:_bool_=False)->_str_:
> Runs a windows command on the remote server.
   - Args:
      - **cmd** *(str)*: Windows command to be executed.
      - **capture_error** *(bool)*: **False** by default, if set to **True**, any error resulted from the execution of the windows command is raised instead.

   - Returns
      - **str**: Standard out or standard error in case of error when **capture_error** is **True**.

   - Raises
     - **OSError**: Raised when the resulted status code is different than **0**_(zero)_ and **capture_error** is **False**.

### powershell(script:_str_, capture_error:_bool_=False)->_str_:
> Executes a powershell script on the remote server.
   - Args
      - **script** _(str)_: Powershell script to be executed.
      - **capture_error** _(bool)_: **False** by default - if set to **True**, any error resulted from the execution of the powershell script is raised instead.

   - Returns
      - str: Standard out or standard error in case of error when **capture_error** is **True**.

   - Raises
      - **OSError**: Raised when the resulted status code is different than **0**_(zero)_ and **capture_error** is **False**.

### ping(host:_str_, packets:_int_=2)->_bool_: 
> Pings a host from the remote server.
   - Args
      - **host** _(str)_: IP address to ping.
      - **packets** _(int)_: Quantity of packets to send. 2 by default. 

   - Returns
      - **bool**: **False** if all packets sent are lost, **True** otherwise.

   - Raises
      - **OSError**: Raised when the resulted status code is different than **0**_(zero)_.

### shut_down(force:_bool_=False): 
> Shuts down the remote server.
   - Args
      - **force** _(bool)_: **False** by default - if set to **True**, the process will be forced.

   - Raises
      - **OSError**: Raised when the resulted status code is different than **0**_(zero)_.

### restart(force:_bool_=False): 
> Restarts the remote server.
   - Args
      - **force** _(bool)_: **False** by default - if set to **True**, the process will be forced.

   - Raises
      - **OSError**: Raised when the resulted status code is different than **0**_(zero)_.

### manage_services()->_WindowsRemoteServer.\_\_ServiceManager_: 
> Returns the service manager object for managing services on the remote server.
   - Returns
      - **WindowsRemoteServer.\_\_ServiceManager**: Service manager object.
         #### get(name:_str_)->_WindowsRemoteServer.\_\_ServiceManager.\_\_Service_:
         > Gets a service instance object by its name.

         - Args
            - **name** _(str)_: Name of the service to get.

         - Returns
            - **WindowsRemoteServer.\_\_ServiceManager.\_\_Service**: Service instance object.
               #### start():
               > Starts the service.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### stop(force:_bool_=False):
               > Stops the service.

               - Args
                  - **force** _(bool)_: Used to define whether or not to force the process. Default is **False**.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### suspend():
               > Suspends the service.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### restart(force:_bool_=False):
               > Restarts the service.

               - Args
                  - **force** _(bool)_: Used to define whether or not to force the process. Default is _False_.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### resume():
               > Resumes the service.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### get_status()->_str_:
               > Returns the service current status.

               - Returns
                  - **str**: Current status.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### get_name()->_str_:
               > Returns the service name.

               - Returns
                  - **str**: Service name.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### is_running()->_bool_:
               > Checks if the service is running.

               - Returns
                  - **bool**: **True** if the service is **running**, otherwise, **False**.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### is_stopped()->_bool_:
               > Checks if the service is stopped.

               - Returns
                  - **bool**: **True** if the service is **stopped**, otherwise, **False**.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### is_paused()->_bool_:
               > Checks if the service is paused.

               - Returns
                  - **bool**: **True** if the service is **paused**, otherwise, **False**.

               - Raises
                  - **OSError**: Raised in case of error.
               
               #### requires()->_list_:
               > Returns a list of service names that is required by this service.

               - Returns
                  - _list_: List of service names that is required by this service.

               - Raises
                  - **OSError**: Raised in case of error.
                             
         - Raises
            - **OSError**: Raised in case of error.

### manage_processes()->_WindowsRemoteServer.\_\_ProcessManager_: 
> Returns the process manager object for managing processes on the remote server.
   - Returns
      - **WindowsRemoteServer.\_\_ProcessManager**: Process manager object.
         #### stop_by_id(\*ids, \*\*kwargs):
         > Stops processes by their ids.
         - Args
            - **\*ids**: Argument list of ids.
            - **\*\*kwargs**: Arbitrary keyword arguments. 

         - Keyword Args
            - **force** _(bool)_: Used to define whether or not to force the stopping process(es).

         - Raises
            - **OSError**: Raised in case of error.
         
         #### stop_by_name(\*names:_str_, \*\*kwargs):
         > Stops processes by their names.
         - Args
            - **\*ids**: Argument list of names. Asterisks (\*) can be used as wildcards.
            - **\*\*kwargs**: Arbitrary keyword arguments. 

         - Keyword Args
            - **force** _(bool)_: Used to define whether or not to force the stopping process(es).

         - Raises
            - **OSError**: Raised in case of error.
         
         #### stop_all_not_responding(force:_bool_=False):
         > Stops all not-responding processes.
         - Args
            - **force** _(bool)_: Used to define whether or not to force the stopping process(es). Default is **False**.

         - Raises
            - **OSError**: Raised in case of error.
         
         #### start(file_path:_str_, \*\*kwargs)->_str_: 
         > Starts a process.
         [See reference](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Start-Process?view=powershell-7.1).

         - Args
            - **file_path** _(str)_: Specifies the path and filename of the program that runs in the process. Enter the name of an executable file or of a document, such as a .txt or .doc file, that is associated with a program on the computer. If you specify only a filename, use the working_directory keyword argument to specify the path.
            - **\*\*kwargs**: Arbitrary keyword arguments. 

         - Keyword Args
            - **args** _(list|tuple)_: Specifies parameters or parameter values to use when this method starts the process
            - **working_directory** _(str)_: Specifies the location that the new process should start in. The default is the location of the executable file or document being started. Wildcards are not supported. The path name must not contain characters that would be interpreted as wildcards.
            - **verb** _(str)_: Specifies a verb to use when starting the process. The verbs that are available are determined by the filename extension of the file that runs in the process.
            - **redirect_stdin** _(str)_: Specifies a file for reading input from it. Enter the path and filename of the input file.
            - **redirect_stdout** _(str)_: Specifies a file to send the output generated by the process to. Enter the path and filename. By default, the output is returned as a string.
            - **redirect_stderr** _(str)_: Specifies a file to send any errors generated by the process to. Enter the path and filename. By default, errors are raised.
            - **window_style** _(str)_: Specifies the state of the window that is used for the new process. The acceptable values for this parameter are: **Normal**, **Hidden**, **Minimized**, and **Maximized**. The default value is **Normal**.
            - **no_new_window** _(bool)_: If **True**, starts the new process in the current console window. If specified, the **window_style** param will be ignored.
            - **pass_through** _(bool)_: Returns, in the standard out, the process object.
            - **load_user_profile** _(bool)_: Loads the Windows user profile stored in the HKEY_USERS registry key for the current user.
            - **wait** _(bool)_: If **True**, waits for the specified process and its descendants to complete before accepting more input. This parameter suppresses the command prompt or retains the window until the processes finish.
            - **use_new_environment** _(bool)_: If **True**, uses new environment variables specified for the process. By default, the started process runs with the environment variables inherited from the parent process.

         - Returns
            - **str**: Standard out. Empty string if the keyword argument pass_through is not found or equivalent to **False**.

         - Raises
            - **OSError**: Raised in case of error.
         
         #### get_extention_verbs(ext:_str_)->_list_:
         > Retrieves a list of verbs available for a given extention.

         - Args
            - **ext** _(str)_: File extention.

         - Returns
            - **list**: List of verbs available for the given extention.

         - Raises
            - **OSError**: Raised in case of error.
         
         #### output(\*include:_str_, \*\*kwargs)->_str_:
         > Outputs a standard powershell table with the processes. Default columns are **Name** and **Memory**.

         - Args
            - **\*include**: Argument list of properties to include. Asterisks (\*) can be used as wildcards. Custom properties will be included between the **Name** and **Memory** columns.
            - **\*\*kwargs**: Arbitrary keyword arguments. 

         - Keyword Args
            - **sort** _(str|list|tuple)_: Used for specifying a sorting logic. As a _string_, it must match a property name. As a _list_ or _tuple_, the first element will define the property name to sort by and the second one will define the order. Consider **-1** or **'desc'** or **'descending'** for descending. Default order is ascending.
            - **limit** _(int)_: Used for limiting the number of rows for the table.
            - **unit** _(str)_: Used to specify a unit for the memory column. Default is **'MB'**. Accepted values are **'KB'**, **'MB'**, **'GB'** and **'TB'** _(case insensitive)_.

         - Returns
            - **str**: Standard powershell table.

         - Raises
            - **OSError**: Raised in case of error.

### bios(*properties:str, **kwargs)->dict: 
Returns the remote server bios data.

### desktop_settings(*properties, **kwargs)->list: 
Returns the remote server descktop settings data.

### computer_system(*properties,**kwargs)->dict: 
Returns the remote server computer system data.

### operating_system(*properties, **kwargs)->dict: 
Returns the remote server operating system data.

### logon_session(*properties, **kwargs)->dict: 
Returns the remote server logon session data.

### local_time(*properties, **kwargs)->dict: 
Returns the current local time data on the remote server.

### processor(*properties, **kwargs)->dict: 
Returns the remote server processor data.

### volumes(*properties, **kwargs)->list: 
Returns a list of all remote server volumes data.

### retrieve_data_from_ps_list(stdout:str)->list: 
Static method that converts standard powershell list to python list of dictionaries.

## Dependencies
- **winrm**: This class relies on the usage of winrm to connect to a remote server and run commands and powershell scripts on it.
