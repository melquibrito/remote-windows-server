# Remote Windows Server Library

## Description
This library provides a class with handy methods for running windows commands, executing powershell scripts, managing services, managing processes and getting information on windows remote servers.

### Getting started
1. Installing:
```
pip install rwin
```
> All [dependencies](#dependencies) are installed automatically if not found.
2. Importing:
``` python
from rwin import RemoteWindowsServer
``` 
3. Connecting to a remote windows server
``` python
server = RemoteWindowsServer("255.255.10.10","user","passward")
```
## Dependencies
- [**winrm**](https://docs.microsoft.com/en-us/windows/win32/winrm/portal): This library relies on the usage of winrm to connect to remote servers and run commands and powershell scripts on them.

## Resources

* [run](#runcmdstr-capture_errorboolfalse-str)
* [powershell](#powershellscriptstr-capture_errorboolfalse-str)
* [ping](#pinghoststr-packetsint2-bool)
* [shut_down](#pinghoststr-packetsint2-bool)
* [restart](#restartforceboolfalse)
* [manage_services](#manage_services-RemoteWindowsServer__servicemanager)
   * [get](#getnamestr-RemoteWindowsServer__servicemanager__service)
      * [start](#start)
      * [stop](#stopforceboolfalse)
      * [suspend](#suspend)
      * [restart](#restartforceboolfalse-1)
      * [resume](#resume)
      * [get_status](#get_status-str)
      * [get_name](#get_name-str)
      * [is_running](#is_running-bool)
      * [is_stopped](#is_stopped-bool)
      * [is_paused](#is_paused-bool)
      * [requires](#requires-list)
      * [dependents](#dependents-list)
      * [get_display_name](#get_display_name-str)
      * [get_service_type](#get_service_type-str)
      * [get_startup_type](#get_startup_type-str)
      * [set_startup_type](#set_startup_typetypestr)
      * [can_pause_and_continue](#can_pause_and_continue-bool)
      * [can_stop](#can_stop-bool)
      * [can_shut_down](#can_shut_down-bool)
   * [has](#hasnamestr-bool)
   * [output](#outputincludestr-kwargs-str) 
* [manage_processes](#manage_processes-RemoteWindowsServer__processmanager)
   * [stop_by_id](#stop_by_idids-kwargs) 
   * [stop_by_name](#stop_by_namenamesstr-kwargs) 
   * [stop_all_not_responding](#stop_all_not_respondingforceboolfalse) 
   * [start](#startfile_pathstr-kwargs-str) 
   * [get_extention_verbs](#get_extention_verbsextstr-list)
   * [output](#outputincludestr-kwargs-str-1)
* [bios](#biospropertiesstr-kwargs-dict)
* [desktop_settings](#desktop_settingspropertiesstr-kwargs-list)
* [computer_system](#computer_systempropertiesstrkwargs-dict)
* [operating_system](#operating_systempropertiesstr-kwargs-dict)
* [logon_session](#logon_sessionpropertiesstr-kwargs-dict)
* [local_time](#local_timepropertiesstr-kwargs-dict)
* [processor](#processorpropertiesstr-kwargs-dict)
* [volumes](#volumespropertiesstr-kwargs-list)
* [retrieve_data_from_ps_list](#retrieve_data_from_ps_liststdoutstr-list)

### run(cmd:_str_, capture_error:_bool_=False)->_str_:
>Runs a windows command on the remote server.
- Args:
   - **cmd** *(str)*: Windows command to be executed.
   - **capture_error** *(bool)*: **False** by default, if set to **True**, standard error will be returned in case of error.

- Returns
   - **str**: Standard out or standard error in case of error when **capture_error** is **True**.

- Raises
  - **OSError**: Raised when the resulted status code is different than **0**_(zero)_ and **capture_error** is **False**.

### powershell(script:_str_, capture_error:_bool_=False)->_str_:
> Executes a powershell script on the remote server.
- Args
   - **script** _(str)_: Powershell script to be executed.
   - **capture_error** _(bool)_: **False** by default - if set to **True**, standard error will be returned in case of error.

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

### manage_services()->_RemoteWindowsServer.\_\_ServiceManager_: 
> Returns the service manager object for managing services on the remote server.
- Returns
   - **RemoteWindowsServer.\_\_ServiceManager**: Service manager object.
      #### get(name:_str_)->_RemoteWindowsServer.\_\_ServiceManager.\_\_Service_:
      > Gets a service instance object by its name.

      - Args
         - **name** _(str)_: Name of the service to get.

      - Returns
         - **RemoteWindowsServer.\_\_ServiceManager.\_\_Service**: Service instance object.
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
               - **bool**: **True** if the service is _running_, otherwise, **False**.

            - Raises
               - **OSError**: Raised in case of error.

            #### is_stopped()->_bool_:
            > Checks if the service is stopped.

            - Returns
               - **bool**: **True** if the service is _stopped_, otherwise, **False**.

            - Raises
               - **OSError**: Raised in case of error.

            #### is_paused()->_bool_:
            > Checks if the service is paused.

            - Returns
               - **bool**: **True** if the service is _paused_, otherwise, **False**.

            - Raises
               - **OSError**: Raised in case of error.

            #### requires()->_list_:
            > Returns a list of service names that is required by this service.

            - Returns
               - _list_: List of service names that is required by this service.

            - Raises
               - **OSError**: Raised in case of error.

            #### dependents()->_list_:
            > Returns a list of service names that depends on this service.

            - Returns
               - **list**: List of service names that depends on this service.

            - Raises
               - **OSError**: Raised in case of error.

            #### get_display_name()->_str_:
            > Returns the display name.

            - Returns
               - **str**: Display name.

            - Raises
               - **OSError**: Raised in case of error.

            #### get_service_type()->_str_:
            > Returns the service type.

            - Returns
               - **str**: Service type.

            - Raises
               - **OSError**: Raised in case of error.

            #### get_startup_type()->_str_:
            > Returns the startup type.

            - Returns
               - **str**: Startup type.

            - Raises
               - **OSError**: Raised in case of error.

            #### set_startup_type(type:_str_):
            > Sets the Startup Type.

            - Args
               - **type** _(str)_: Type name ('Boot'|'System'|'Automatic'|'Manual'|'Disabled').

            - Raises
               - **OSError**: Raised in case of error.

            #### can_pause_and_continue()->bool:
            > Checks if this service can be paused.

            - Returns
               - **bool**: **True** if this service can be paused, otherwise, **False**.

            - Raises
               - **OSError**: Raised in case of error.

            #### can_stop()->_bool_:
            > Checks if this service can be stopped.

            - Returns
               - **bool**: **True** if this service can be stopped, otherwise, **False**.

            - Raises
               - **OSError**: Raised in case of error.

            #### can_shut_down()->_bool_:
            > Checks if this service is notified when the system is shutting down.

            - Returns
               - **bool**: **True** if this service is notified when the system is shutting down, otherwise, **False**.

            - Raises
               - **OSError**: Raised in case of error.

      - Raises
         - **OSError**: Raised in case of error.

      #### has(name:_str_)->_bool_:
      > Checks if a service exists.

      - Args
         - **name** _(str)_: The name of a service.

      - Returns
         - **bool**: **True** if the service exists, **False** otherwise.
      
      #### output(\*include:_str_, \*\*kwargs)->_str_:
      > Outputs a standard powershell table with the services. Default columns are **Status**, **Name** and **DisplayName**.

      - Args
         - **\*include**: Argument list of properties to include. Asterisks (\*) can be used as wildcards. Custom properties will be included to the right of DisplayName.
         - **\*\*kwargs**: Arbitrary keyword arguments. 

      - Keyword Args
         - **sort** _(str|list|tuple)_: Used for specifying a sorting logic. As a _string_, it must match a property name. As a _list_ or _tuple_, the first element will define the property name to sort by and the second one will define the order. Consider **-1** or **'desc'** or **'descending'** for descending. Default order is ascending.
         - **limit** _(int)_: Used for limiting the number of rows for the table.

      - Returns
         - **str**: Standard powershell table.

      - Raises
         - **OSError**: Raised in case of error.

### manage_processes()->_RemoteWindowsServer.\_\_ProcessManager_: 
> Returns the process manager object for managing processes on the remote server.
- Returns
   - **RemoteWindowsServer.\_\_ProcessManager**: Process manager object.
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

### bios(\*properties:_str_, \*\*kwargs)->_dict_: 
> Returns a dictionary with bios data.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default dictionary.

- Returns
   - **dict**: Bios data. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      * Status
      * Name
      * Caption
      * SMBIOSPresent
      * Description
      * InstallDate
      * BuildNumber
      * CodeSet
      * IdentificationCode
      * LanguageEdition
      * Manufacturer
      * OtherTargetOS
      * SerialNumber
      * SoftwareElementID
      * SoftwareElementState
      * TargetOperatingSystem
      * Version
      * PrimaryBIOS
      * BiosCharacteristics
      * BIOSVersion
      * CurrentLanguage
      * EmbeddedControllerMajorVersion
      * EmbeddedControllerMinorVersion
      * InstallableLanguages
      * ListOfLanguages
      * ReleaseDate
      * SMBIOSBIOSVersion
      * SMBIOSMajorVersion
      * SMBIOSMinorVersion
      * SystemBiosMajorVersion
      * SystemBiosMinorVersion
      * PSComputerName
      * CimClass
      * CimInstanceProperties
      * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### desktop_settings(\*properties:_str_, \*\*kwargs)->_list_: 
> Returns a list of dictionaries with all descktops settings.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default list of dictionaries.

- Returns
   - list: List of descktops settings. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      - dict:
          * Name
          * ScreenSaverActive
          * Caption
          * Description
          * SettingID
          * BorderWidth
          * CoolSwitch
          * CursorBlinkRate
          * DragFullWindows
          * GridGranularity
          * IconSpacing
          * IconTitleFaceName
          * IconTitleSize
          * IconTitleWrap
          * Pattern
          * ScreenSaverExecutable
          * ScreenSaverSecure
          * ScreenSaverTimeout
          * Wallpaper
          * WallpaperStretched
          * WallpaperTiled
          * PSComputerName
          * CimClass
          * CimInstanceProperties
          * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### computer_system(\*properties:_str_,\*\*kwargs)->_dict_: 
> Returns a dictionary with information about the computer system.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default dictionary.

- Returns
   - **dict**: Computer system data. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      * AdminPasswordStatus
      * BootupState
      * ChassisBootupState
      * KeyboardPasswordStatus
      * PowerOnPasswordStatus
      * PowerSupplyState
      * PowerState
      * FrontPanelResetStatus
      * ThermalState
      * Status
      * Name
      * PowerManagementCapabilities
      * PowerManagementSupported
      * Caption
      * Description
      * InstallDate
      * CreationClassName
      * NameFormat
      * PrimaryOwnerContact
      * PrimaryOwnerName
      * Roles
      * InitialLoadInfo
      * LastLoadInfo
      * ResetCapability
      * AutomaticManagedPagefile
      * AutomaticResetBootOption
      * AutomaticResetCapability
      * BootOptionOnLimit
      * BootOptionOnWatchDog
      * BootROMSupported
      * BootStatus
      * ChassisSKUNumber
      * CurrentTimeZone
      * DaylightInEffect
      * DNSHostName
      * Domain
      * DomainRole
      * EnableDaylightSavingsTime
      * HypervisorPresent
      * InfraredSupported
      * Manufacturer
      * Model
      * NetworkServerModeEnabled
      * NumberOfLogicalProcessors
      * NumberOfProcessors
      * OEMLogoBitmap
      * OEMStringArray
      * PartOfDomain
      * PauseAfterReset
      * PCSystemType
      * PCSystemTypeEx
      * ResetCount
      * ResetLimit
      * SupportContactDescription
      * SystemFamily
      * SystemSKUNumber
      * SystemStartupDelay
      * SystemStartupOptions
      * SystemStartupSetting
      * SystemType
      * TotalPhysicalMemory
      * UserName
      * WakeUpType
      * Workgroup
      * PSComputerName
      * CimClass
      * CimInstanceProperties
      * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### operating_system(\*properties:_str_, \*\*kwargs)->_dict_: 
> Returns a dictionary with information about the OS installed.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default dictionary.

- Returns
   - **dict**: Operating system data. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      * FreePhysicalMemory
      * FreeSpaceInPagingFiles
      * FreeVirtualMemory
      * Caption
      * Description
      * InstallDate
      * CreationClassName
      * CSCreationClassName
      * CSName
      * CurrentTimeZone
      * Distributed
      * LastBootUpTime
      * LocalDateTime
      * MaxNumberOfProcesses
      * MaxProcessMemorySize
      * NumberOfLicensedUsers
      * NumberOfProcesses
      * NumberOfUsers
      * OSType
      * OtherTypeDescription
      * SizeStoredInPagingFiles
      * TotalSwapSpaceSize
      * TotalVirtualMemorySize
      * TotalVisibleMemorySize
      * Version
      * BootDevice
      * BuildNumber
      * BuildType
      * CodeSet
      * CountryCode
      * CSDVersion
      * DataExecutionPrevention_32BitApplications
      * DataExecutionPrevention_Available
      * DataExecutionPrevention_Drivers
      * DataExecutionPrevention_SupportPolicy
      * Debug
      * EncryptionLevel
      * ForegroundApplicationBoost
      * LargeSystemCache
      * Locale
      * Manufacturer
      * MUILanguages
      * OperatingSystemSKU
      * Organization
      * OSArchitecture
      * OSLanguage
      * OSProductSuite
      * PAEEnabled
      * PlusProductID
      * PlusVersionNumber
      * PortableOperatingSystem
      * Primary
      * ProductType
      * RegisteredUser
      * SerialNumber
      * ServicePackMajorVersion
      * ServicePackMinorVersion
      * SuiteMask
      * SystemDevice
      * SystemDirectory
      * SystemDrive
      * WindowsDirectory
      * PSComputerName
      * CimClass
      * CimInstanceProperties
      * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### logon_session(\*properties:_str_, \*\*kwargs)->_dict_: 
> Returns a dictionary with information about the current logon session.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default dictionary.

- Returns
   - **dict**: Logon session data. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      * Caption
      * Description
      * InstallDate
      * Name
      * Status
      * StartTime
      * AuthenticationPackage
      * LogonId
      * LogonType
      * PSComputerName
      * CimClass
      * CimInstanceProperties
      * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### local_time(\*properties:_str_, \*\*kwargs)->_dict_: 
> Returns a dictionary with current local time data.server.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default dictionary.

- Returns
   - **dict**: Local time data. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      * Day
      * DayOfWeek
      * Hour
      * Milliseconds
      * Minute
      * Month
      * Quarter
      * Second
      * WeekInMonth
      * Year
      * PSComputerName
      * CimClass
      * CimInstanceProperties
      * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### processor(\*properties:_str_, \*\*kwargs)->_dict_: 
> Returns a dictionary with information about the processor.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default dictionary.

- Returns
   - **dict**: Processor data. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      * Availability
      * CpuStatus
      * CurrentVoltage
      * DeviceID
      * ErrorCleared
      * ErrorDescription
      * LastErrorCode
      * LoadPercentage
      * Status
      * StatusInfo
      * AddressWidth
      * DataWidth
      * ExtClock
      * L2CacheSize
      * L2CacheSpeed
      * MaxClockSpeed
      * PowerManagementSupported
      * ProcessorType
      * Revision
      * SocketDesignation
      * Version
      * VoltageCaps
      * Caption
      * Description
      * InstallDate
      * Name
      * ConfigManagerErrorCode
      * ConfigManagerUserConfig
      * CreationClassName
      * PNPDeviceID
      * PowerManagementCapabilities
      * SystemCreationClassName
      * SystemName
      * CurrentClockSpeed
      * Family
      * OtherFamilyDescription
      * Role
      * Stepping
      * UniqueId
      * UpgradeMethod
      * Architecture
      * AssetTag
      * Characteristics
      * L3CacheSize
      * L3CacheSpeed
      * Level
      * Manufacturer
      * NumberOfCores
      * NumberOfEnabledCore
      * NumberOfLogicalProcessors
      * PartNumber
      * ProcessorId
      * SecondLevelAddressTranslationExtensions
      * SerialNumber
      * ThreadCount
      * VirtualizationFirmwareEnabled
      * VMMonitorModeExtensions
      * PSComputerName
      * CimClass
      * CimInstanceProperties
      * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### volumes(\*properties:_str_, \*\*kwargs)->_list_: 
> Returns a list of dictionaries with all volumes available or connected to the server.
- Args
   - **\*properties** _(str)_: Argument list of properties to return. Asterisks (\*) can be used as wildcards.
   - **\*\*kwargs**: Arbitrary keyword arguments. 

- Keyword Args
   - **raw** _(bool)_: Used to define whether or not to return the raw standard out instead of the default list of dictionaries.

- Returns
   - **list**: List of volumes. The standard out _string_ may be returned instead if **raw** is found in the _keyword arguments_ and equivalent to **True**.
      - **dict**:
          * Status
          * Availability
          * DeviceID
          * StatusInfo
          * Caption
          * Description
          * InstallDate
          * Name
          * ConfigManagerErrorCode
          * ConfigManagerUserConfig
          * CreationClassName
          * ErrorCleared
          * ErrorDescription
          * LastErrorCode
          * PNPDeviceID
          * PowerManagementCapabilities
          * PowerManagementSupported
          * SystemCreationClassName
          * SystemName
          * Access
          * BlockSize
          * ErrorMethodology
          * NumberOfBlocks
          * Purpose
          * FreeSpace
          * Size
          * Compressed
          * DriveType
          * FileSystem
          * MaximumComponentLength
          * MediaType
          * ProviderName
          * QuotasDisabled
          * QuotasIncomplete
          * QuotasRebuilding
          * SupportsDiskQuotas
          * SupportsFileBasedCompression
          * VolumeDirty
          * VolumeName
          * VolumeSerialNumber
          * PSComputerName
          * CimClass
          * CimInstanceProperties
          * CimSystemProperties

- Raises
   - **OSError**: Raised in case of error.

### retrieve_data_from_ps_list(stdout:_str_)->_list_: 
> Static method that converts standard powershell list to python list of dictionaries.
- Args
   - **stdout** _(str)_: Powershell list-formatted standard out.

- Returns
   - **list**: List of items.
      - **dict**: Item.

## Author
* [Melqui Brito](https://github.com/melquibrito)

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for more details.
