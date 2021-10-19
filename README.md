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
         Reference: https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Start-Process?view=powershell-7.1

         - Args
            - **file_path** _(str)_: Specifies the path and filename of the program that runs in the process. Enter the name of an executable file or of a document, such as a .txt or .doc file, that is associated with a program on the computer. If you specify only a filename, use the working_directory keyword argument to specify the path.
            - \*\*kwargs: Arbitrary keyword arguments. 

         - Keyword Args
            - **args** _(list|tuple)_: Specifies parameters or parameter values to use when this method starts the process
            - **working_directory** _(str)_:
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
