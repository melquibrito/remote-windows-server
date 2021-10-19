# Windows Remote Server Library

class WindowsRemoteServer(builtins.object)
 |  WindowsRemoteServer(host: str, username: str, password: str, port: int = 5985)
 |
 |  This class defines a remote windows server connection session providing methods for running windows commands and powershell scripts alongside built-in methods for common tasks.
 |
 |  Methods
 |  -------
 |  - run(cmd:str, capture_error:bool=False)->str: Runs a windows command on the remote server.
 |  - powershell(script:str, capture_error:bool=False)->str: Executes a powershell script on the remote server.
 |  - ping(host:str, packets:int=2)->bool: Pings a host from the remote server.
 |  - shut_down(force=False): Shuts down the remote server.
 |  - restart(force=False): Restarts the remote server.
 |  - manage_services()->WindowsRemoteServer.__ServiceManager: Returns the service manager object for managing services on the remote server.
 |  - manage_processes()->WindowsRemoteServer.__ProcessManager: Returns the process manager object for managing processes on the remote server.
 |  - bios(*properties:str, **kwargs)->dict: Returns the remote server bios data.
 |  - desktop_settings(*properties, **kwargs)->list: Returns the remote server descktop settings data.
 |  - computer_system(*properties,**kwargs)->dict: Returns the remote server computer system data.
 |  - operating_system(*properties, **kwargs)->dict: Returns the remote server operating system data.
 |  - logon_session(*properties, **kwargs)->dict: Returns the remote server logon session data.
 |  - local_time(*properties, **kwargs)->dict: Returns the current local time data on the remote server.
 |  - processor(*properties, **kwargs)->dict: Returns the remote server processor data.
 |  - volumes(*properties, **kwargs)->list: Returns a list of all remote server volumes data.
 |  - retrieve_data_from_ps_list(stdout:str)->list: Static method that converts standard powershell list to python list of dictionaries.
 |
 |  Dependencies
 |  ------------
 |  - winrm: This class relies on the usage of winrm to connect to a remote server and run commands and powershell scripts on it.
 |
 |  Methods defined here:
 |
 |  __dict__ = mappingproxy({'__module__': 'windows_remote_serv...'__weakref__' of 'WindowsRemoteServer' objects>})
 |  __getitem__(self, key)
 |
 |  __init__(self, host: str, username: str, password: str, port: int = 5985)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |
 |  __str__(self) -> str
 |      Return str(self).
 |
 |  bios(self, *properties: str, **kwargs) -> dict
 |      Remote server bios data.
 |
 |      Args
 |      ----
 |      - *properties (str): Argument list of properties to return. Asterisks (*) can be used as wildcards.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default dictionary.
 |
 |      Returns
 |      -------
 |      - dict: Bios data. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          * Status
 |          * Name
 |          * Caption
 |          * SMBIOSPresent
 |          * Description
 |          * InstallDate
 |          * BuildNumber
 |          * CodeSet
 |          * IdentificationCode
 |          * LanguageEdition
 |          * Manufacturer
 |          * OtherTargetOS
 |          * SerialNumber
 |          * SoftwareElementID
 |          * SoftwareElementState
 |          * TargetOperatingSystem
 |          * Version
 |          * PrimaryBIOS
 |          * BiosCharacteristics
 |          * BIOSVersion
 |          * CurrentLanguage
 |          * EmbeddedControllerMajorVersion
 |          * EmbeddedControllerMinorVersion
 |          * InstallableLanguages
 |          * ListOfLanguages
 |          * ReleaseDate
 |          * SMBIOSBIOSVersion
 |          * SMBIOSMajorVersion
 |          * SMBIOSMinorVersion
 |          * SystemBiosMajorVersion
 |          * SystemBiosMinorVersion
 |          * PSComputerName
 |          * CimClass
 |          * CimInstanceProperties
 |          * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  computer_system(self, *properties, **kwargs) -> dict
 |      Remote server computer system data.
 |
 |      Args
 |      ----
 |      - *properties (str): Argument list of properties to return. Asterisks (*) can be used as wildcards.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default dictionary.
 |
 |      Returns
 |      -------
 |      - dict: Computer system data. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          * AdminPasswordStatus
 |          * BootupState
 |          * ChassisBootupState
 |          * KeyboardPasswordStatus
 |          * PowerOnPasswordStatus
 |          * PowerSupplyState
 |          * PowerState
 |          * FrontPanelResetStatus
 |          * ThermalState
 |          * Status
 |          * Name
 |          * PowerManagementCapabilities
 |          * PowerManagementSupported
 |          * Caption
 |          * Description
 |          * InstallDate
 |          * CreationClassName
 |          * NameFormat
 |          * PrimaryOwnerContact
 |          * PrimaryOwnerName
 |          * Roles
 |          * InitialLoadInfo
 |          * LastLoadInfo
 |          * ResetCapability
 |          * AutomaticManagedPagefile
 |          * AutomaticResetBootOption
 |          * AutomaticResetCapability
 |          * BootOptionOnLimit
 |          * BootOptionOnWatchDog
 |          * BootROMSupported
 |          * BootStatus
 |          * ChassisSKUNumber
 |          * CurrentTimeZone
 |          * DaylightInEffect
 |          * DNSHostName
 |          * Domain
 |          * DomainRole
 |          * EnableDaylightSavingsTime
 |          * HypervisorPresent
 |          * InfraredSupported
 |          * Manufacturer
 |          * Model
 |          * NetworkServerModeEnabled
 |          * NumberOfLogicalProcessors
 |          * NumberOfProcessors
 |          * OEMLogoBitmap
 |          * OEMStringArray
 |          * PartOfDomain
 |          * PauseAfterReset
 |          * PCSystemType
 |          * PCSystemTypeEx
 |          * ResetCount
 |          * ResetLimit
 |          * SupportContactDescription
 |          * SystemFamily
 |          * SystemSKUNumber
 |          * SystemStartupDelay
 |          * SystemStartupOptions
 |          * SystemStartupSetting
 |          * SystemType
 |          * TotalPhysicalMemory
 |          * UserName
 |          * WakeUpType
 |          * Workgroup
 |          * PSComputerName
 |          * CimClass
 |          * CimInstanceProperties
 |          * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  desktop_settings(self, *properties, **kwargs) -> list
 |      Remote server descktop settings data.
 |
 |      Args
 |      ----
 |      - *properties (str): Argument list of properties to return. Asterisks (*) can be used as wildcards.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default list of dictionaries.
 |
 |      Returns
 |      -------
 |      - list: List of descktops settings. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          - dict
 |              * Name
 |              * ScreenSaverActive
 |              * Caption
 |              * Description
 |              * SettingID
 |              * BorderWidth
 |              * CoolSwitch
 |              * CursorBlinkRate
 |              * DragFullWindows
 |              * GridGranularity
 |              * IconSpacing
 |              * IconTitleFaceName
 |              * IconTitleSize
 |              * IconTitleWrap
 |              * Pattern
 |              * ScreenSaverExecutable
 |              * ScreenSaverSecure
 |              * ScreenSaverTimeout
 |              * Wallpaper
 |              * WallpaperStretched
 |              * WallpaperTiled
 |              * PSComputerName
 |              * CimClass
 |              * CimInstanceProperties
 |              * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  local_time(self, *properties, **kwargs) -> dict
 |      Current local time data on the remote server.
 |
 |      Args
 |      ----
 |      - *properties (str): Properties to fetch - if none is found, all properties will be fetched.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default dictionary.
 |
 |      Returns
 |      -------
 |      - dict: Local time data. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          * Day
 |          * DayOfWeek
 |          * Hour
 |          * Milliseconds
 |          * Minute
 |          * Month
 |          * Quarter
 |          * Second
 |          * WeekInMonth
 |          * Year
 |          * PSComputerName
 |          * CimClass
 |          * CimInstanceProperties
 |          * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  logon_session(self, *properties, **kwargs) -> dict
 |      Remote server logon session data.
 |
 |      Args
 |      ----
 |      - *properties (str): Properties to fetch - if none is found, all properties will be fetched.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default dictionary.
 |
 |      Returns
 |      -------
 |      - dict: Logon session data. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          * Caption
 |          * Description
 |          * InstallDate
 |          * Name
 |          * Status
 |          * StartTime
 |          * AuthenticationPackage
 |          * LogonId
 |          * LogonType
 |          * PSComputerName
 |          * CimClass
 |          * CimInstanceProperties
 |          * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  manage_processes(self) -> 'WindowsRemoteServer.__ProcessManager'
 |      Returns the process manager object for managing processes on the remote server.
 |
 |      Returns
 |      -------
 |      - WindowsRemoteServer.__ProcessManager: Process manager object.
 |
 |  manage_services(self) -> 'WindowsRemoteServer.__ServiceManager'
 |      Returns the service manager object for managing services on the remote server.
 |
 |      Returns
 |      -------
 |      - WindowsRemoteServer.__ServiceManager: Service manager object.
 |
 |  operating_system(self, *properties, **kwargs) -> dict
 |      Remote server operating system data.
 |
 |      Args
 |      ----
 |      - *properties (str): Argument list of properties to return. Asterisks (*) can be used as wildcards.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default dictionary.
 |
 |      Returns
 |      -------
 |      - dict: Operating system data. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          * FreePhysicalMemory
 |          * FreeSpaceInPagingFiles
 |          * FreeVirtualMemory
 |          * Caption
 |          * Description
 |          * InstallDate
 |          * CreationClassName
 |          * CSCreationClassName
 |          * CSName
 |          * CurrentTimeZone
 |          * Distributed
 |          * LastBootUpTime
 |          * LocalDateTime
 |          * MaxNumberOfProcesses
 |          * MaxProcessMemorySize
 |          * NumberOfLicensedUsers
 |          * NumberOfProcesses
 |          * NumberOfUsers
 |          * OSType
 |          * OtherTypeDescription
 |          * SizeStoredInPagingFiles
 |          * TotalSwapSpaceSize
 |          * TotalVirtualMemorySize
 |          * TotalVisibleMemorySize
 |          * Version
 |          * BootDevice
 |          * BuildNumber
 |          * BuildType
 |          * CodeSet
 |          * CountryCode
 |          * CSDVersion
 |          * DataExecutionPrevention_32BitApplications
 |          * DataExecutionPrevention_Available
 |          * DataExecutionPrevention_Drivers
 |          * DataExecutionPrevention_SupportPolicy
 |          * Debug
 |          * EncryptionLevel
 |          * ForegroundApplicationBoost
 |          * LargeSystemCache
 |          * Locale
 |          * Manufacturer
 |          * MUILanguages
 |          * OperatingSystemSKU
 |          * Organization
 |          * OSArchitecture
 |          * OSLanguage
 |          * OSProductSuite
 |          * PAEEnabled
 |          * PlusProductID
 |          * PlusVersionNumber
 |          * PortableOperatingSystem
 |          * Primary
 |          * ProductType
 |          * RegisteredUser
 |          * SerialNumber
 |          * ServicePackMajorVersion
 |          * ServicePackMinorVersion
 |          * SuiteMask
 |          * SystemDevice
 |          * SystemDirectory
 |          * SystemDrive
 |          * WindowsDirectory
 |          * PSComputerName
 |          * CimClass
 |          * CimInstanceProperties
 |          * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  ping(self, host: str, packets: int = 2) -> bool
 |      Pings a host from the remote server.
 |
 |      Args
 |      ----
 |      - host (str): IP address to ping.
 |      - packets (int): Quantity of packets to send. 2 by default.
 |
 |      Returns
 |      -------
 |      - bool: False if all packets sent are lost, True otherwise.
 |
 |      Raises
 |      ------
 |      - OSError: Raised when the resulted status code is different than 0.
 |
 |  powershell(self, script: str, capture_error: bool = False) -> str
 |      Executes a powershell script on the remote server.
 |
 |      Args
 |      ----
 |      - script (str): Powershell script to be executed.
 |      - capture_error (bool): False by default - if set to True, any error resulted from the execution of the powershell script is raised instead.
 |
 |      Returns
 |      -------
 |      - str: Standard out or standard error in case of error when capture_error is True.
 |
 |      Raises
 |      ------
 |      - OSError: Raised when the resulted status code is different than 0 and capture_error is False.
 |
 |  processor(self, *properties, **kwargs) -> dict
 |      Remote server processor data.
 |
 |      Args
 |      ----
 |      - *properties (str): Properties to fetch - if none is found, all properties will be fetched.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default dictionary.
 |
 |      Returns
 |      -------
 |      - dict: Processor data. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          * Availability
 |          * CpuStatus
 |          * CurrentVoltage
 |          * DeviceID
 |          * ErrorCleared
 |          * ErrorDescription
 |          * LastErrorCode
 |          * LoadPercentage
 |          * Status
 |          * StatusInfo
 |          * AddressWidth
 |          * DataWidth
 |          * ExtClock
 |          * L2CacheSize
 |          * L2CacheSpeed
 |          * MaxClockSpeed
 |          * PowerManagementSupported
 |          * ProcessorType
 |          * Revision
 |          * SocketDesignation
 |          * Version
 |          * VoltageCaps
 |          * Caption
 |          * Description
 |          * InstallDate
 |          * Name
 |          * ConfigManagerErrorCode
 |          * ConfigManagerUserConfig
 |          * CreationClassName
 |          * PNPDeviceID
 |          * PowerManagementCapabilities
 |          * SystemCreationClassName
 |          * SystemName
 |          * CurrentClockSpeed
 |          * Family
 |          * OtherFamilyDescription
 |          * Role
 |          * Stepping
 |          * UniqueId
 |          * UpgradeMethod
 |          * Architecture
 |          * AssetTag
 |          * Characteristics
 |          * L3CacheSize
 |          * L3CacheSpeed
 |          * Level
 |          * Manufacturer
 |          * NumberOfCores
 |          * NumberOfEnabledCore
 |          * NumberOfLogicalProcessors
 |          * PartNumber
 |          * ProcessorId
 |          * SecondLevelAddressTranslationExtensions
 |          * SerialNumber
 |          * ThreadCount
 |          * VirtualizationFirmwareEnabled
 |          * VMMonitorModeExtensions
 |          * PSComputerName
 |          * CimClass
 |          * CimInstanceProperties
 |          * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  restart(self, force=False)
 |      Restarts the remote server.
 |
 |      Args
 |      ----
 |      - force (bool): False by default - if set to True, the process will be forced.
 |
 |      Raises
 |      ------
 |      - OSError: Raised when the resulted status code is different than 0.
 |
 |  run(self, cmd: str, capture_error: bool = False) -> str
 |      Runs a windows command on the remote server.
 |
 |      Args
 |      ----
 |      - cmd (str): Windows command to be executed.
 |      - capture_error (bool): False by default, if set to True, any error resulted from the execution of the windows command is raised instead.
 |
 |      Returns
 |      -------
 |      - str: Standard out or standard error in case of error when capture_error is True.
 |
 |      Raises
 |      ------
 |      - OSError: Raised when the resulted status code is different than 0 and capture_error is False.
 |
 |  shut_down(self, force=False)
 |      Shuts down the remote server.
 |
 |      Args
 |      ----
 |      - force (bool): False by default - if set to True, the process will be forced.
 |
 |      Raises
 |      ------
 |      - OSError: Raised when the resulted status code is different than 0.
 |
 |  volumes(self, *properties, **kwargs) -> list
 |      Remote server volumes data.
 |
 |      Args
 |      ----
 |      - *properties (str): Properties to fetch - if none is found, all properties will be fetched.
 |      - **kwargs: Arbitrary keyword arguments.
 |
 |      Keyword Args
 |      ------------
 |      - raw (bool): Used to define whether or not to return the raw standard out instead of the default list of dictionaries.
 |
 |      Returns
 |      -------
 |      - list: List of volumes. The standard out string may be returned instead if raw is found in the keyword arguments and equivalent to True.
 |          - dict:
 |              * Status
 |              * Availability
 |              * DeviceID
 |              * StatusInfo
 |              * Caption
 |              * Description
 |              * InstallDate
 |              * Name
 |              * ConfigManagerErrorCode
 |              * ConfigManagerUserConfig
 |              * CreationClassName
 |              * ErrorCleared
 |              * ErrorDescription
 |              * LastErrorCode
 |              * PNPDeviceID
 |              * PowerManagementCapabilities
 |              * PowerManagementSupported
 |              * SystemCreationClassName
 |              * SystemName
 |              * Access
 |              * BlockSize
 |              * ErrorMethodology
 |              * NumberOfBlocks
 |              * Purpose
 |              * FreeSpace
 |              * Size
 |              * Compressed
 |              * DriveType
 |              * FileSystem
 |              * MaximumComponentLength
 |              * MediaType
 |              * ProviderName
 |              * QuotasDisabled
 |              * QuotasIncomplete
 |              * QuotasRebuilding
 |              * SupportsDiskQuotas
 |              * SupportsFileBasedCompression
 |              * VolumeDirty
 |              * VolumeName
 |              * VolumeSerialNumber
 |              * PSComputerName
 |              * CimClass
 |              * CimInstanceProperties
 |              * CimSystemProperties
 |
 |      Raises
 |      ------
 |      - OSError: Raised in case of error.
 |
 |  ----------------------------------------------------------------------
 |  Static methods defined here:
 |
 |  retrieve_data_from_ps_list(stdout: str) -> list
 |      Converts standard powershell list to python list of dictionaries.
 |
 |      Args
 |      ----
 |      stdout (str): Powershell list-formatted standard out.
 |
 |      Returns
 |      -------
 |      list: List of items.
 |          - dict: Item.
 |

