# Shellcode for creating a minidump-file (.dmp) of lsass.exe

**Purpose:** Created to avoid putting mimikatz directly on the targed system. The shellcode can be incorporated into different projects/exploits etc. 

**Limitations:** The SeDebugPrivilege has to be enabled before using the shellcode. *(Hint: Powershell enables SeDebugPrivileged by default if the current user is allowed to use it i.e the local administrator).*  

**Script:** The script is created in Python3 with the keystone-engine module (pip install keystone-engine)

**Where:** A file named lsass.dmp is created within the directory where the shellcode is executed.

**Fun-fact:** The Win32 API used: MiniDumpWriteDump is located within dbgcore.dll and not dbghelp.dll. For more information [MiniDumpWriteDump according to msdn](https://docs.microsoft.com/en-us/windows/win32/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump)

**Idea:** The idea came from reading this c++ script from [ired.team](https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dumping-lsass-passwords-without-mimikatz-minidumpwritedump-av-signature-bypass) 

**Thanks:** Offensive-Security and their [Exploit Development course Exp-301](https://www.offensive-security.com/exp301-osed/)

## Example:
The script can be executed directly using Python. Otherwise, extract the opcodes and use them in another project. 
![Dumping lsass.exe](/img/First.PNG "Example")

After the lsass.dmp is created, Mimikatz can be used to extract the hashes and/or passwords.
![Extracting using mimikatz](/img/Second.PNG "Example")
