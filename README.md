# Windows Remote Server Library

## Methods
### run(cmd:_str_, capture_error:_bool_=False)->_str_:
Runs a windows command on the remote server.
   - Args:
      - **cmd** *(str)*: Windows command to be executed.
      - **capture_error** *(bool)*: **False** by default, if set to **True**, any error resulted from the execution of the windows command is raised instead.

   - Returns
      - **str**: Standard out or standard error in case of error when **capture_error** is **True**.

   - Raises
     - **OSError**: Raised when the resulted status code is different than **0**_(zero)_ and **capture_error** is **False**.

### powershell(script:_str_, capture_error:_bool_=False)->_str_:
Executes a powershell script on the remote server.

### ping(host:str, packets:int=2)->bool: 
Pings a host from the remote server.

### shut_down(force=False): 
Shuts down the remote server.

### restart(force=False): 
Restarts the remote server.

### manage_services()->WindowsRemoteServer.__ServiceManager: 
Returns the service manager object for managing services on the remote server.

### manage_processes()->WindowsRemoteServer.__ProcessManager: 
Returns the process manager object for managing processes on the remote server.

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
