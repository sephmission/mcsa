# 1 - Install and configure servers

### Install servers

### Configure Servers

- **GUI Off with Powershell**

  You can do the same thing as we did in the GUI much quicker with a PowerShell cmdlet. To do so, open Server Manager, click on Tools and launch PowerShell.

  We can use the Remove-WindowsFeature cmdlet to remove the feature:

  ```
  Remove-WindowsFeature Server-Gui-Shell, Server-Gui-Mgmt-Infra
  ```

  Since Remove-WindowsFeature is just an alias, you could also use:

  ```
  Uninstall-WindowsFeature Server-Gui-Shell, Server-Gui-Mgmt-Infra
  ```

  Not long after you have  hit the enter key, the removal will begin. When it’s done, you will be notified that you need to restart your server to complete the process, which can be easily done from the current PowerShell window by running:

  ```
   Shutdown –r -t 0
  ```

  When your machine restarts you will only have the command line to work with.

  >*Source: http://www.howtogeek.com/111967/how-to-turn-the-gui-off-and-on-in-windows-server-2012/*

- **GUI On with Powershell**

  The first thing we need to do is get into PowerShell, so type PowerShell and hit enter.

  Now we need to use the Add-WindowsFeature to add the components  back:

  ```
  Add-WindowsFeature Server-Gui-Shell, Server-Gui-Mgmt-Infra
  ```

  Again this is just an alias for:

  ```
  Install-WindowsFeature Server-Gui-Shell, Server-Gui-Mgmt-Infra
  ```

  When its done, we will need to restart our server by using the Shutdown command:

  ```
  Shutdown –r -t 0
  ```

  When your server reboots you will have the GUI back.

  >*Source: http://www.howtogeek.com/111967/how-to-turn-the-gui-off-and-on-in-windows-server-2012/*


### Configure local storage
