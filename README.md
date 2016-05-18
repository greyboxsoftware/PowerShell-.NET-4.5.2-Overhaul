# PowerShell-.NET-4.5.2-Overhaul
The following script is a little script I wrote as a .NET 4.5.2 overhaul script

The script will do the following:

  Ask the users for a text file that contains a list of computers
  Test those computers for connectivity and skip if its unpingable
  If the computer is ping able it will then check the WMI to determine version of .NET installed
    If .NET is 4.5.2 then the script outputs it on the terminal then moves on to the next computer in the text file.
  If the computer has a different version installed the script will ask you if you want to bring that computer to compliance of .NET 4.5.2
    This is to ensure that you really want to do it.
  Once you say yes the script will do the following
    determine if c:\temp directory exist on remote computer and if it doesn’t it will create it
    Copy the .NET web installer to remote computer from a share
    copy the .NET uninstaller from a share folder
    copy a cmd file with a list of itemized commands from a share
    Then it will execute the cmd script via a sysInterals
      NOTE: When executing this script have psexec in the working directory that PowerShell is in. I.e. Admin PowerShell is usually defaulted to c:\windows\system32 so have psexec.exe in the system32 directory
    This command script has a list of commands that will run that will remove all versions of .NET Framework then run the web installer to install the .NET 4.5.2
  Once the uninstall/install is complete the script will recheck the .NET version.
