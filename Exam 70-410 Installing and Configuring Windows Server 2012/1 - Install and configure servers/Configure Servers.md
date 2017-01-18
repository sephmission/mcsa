# Configure Servers

## Contents
- [Windows Server 2012 Limits](#windows-limits)
- [Server GUI On and Off](#gui)

## OS Licensing and Server Versioning

### Server 2012 is not available in 32-bit
- Data Center
- Standard
- Essentials (same functionality of standard and web version of Windows Server 2008)
- Foundations

### Differences in Licensing are exposed by the number of users and physical/virtual instances each support.

| EDITION    | POSE INSTANCES   | VOSE INSTANCES   |
| ---------- | ---------------- | ---------------- |
| Datacenter | 1                | Unlimited        |
| Standard.  | 1                | 2                |
| Foundation | 1                | 0                |
| Essentials | 1 (POSE or VOSE) | 1 (POSE or VOSE) |


>*Source: https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx*

<a name="windows-limits"></a>
## Windows Server 2012 Limits

--- | Foundation | Essentials | Standard / Datacenter
--- | --- | --- | ---
Processor Limit | 1 | 2 | 64
RAM | 32GB | 64GB | 4TB
Max users | 15 | 25 | Unlimited
Routing and Remote Access (RRAS) | 50 | 250 | Unlimited
Active Directory Services | Root only | Root only | Full
Active Directory Certificate Services | CA Only | CA Only | Full
Hyper V / Server Core | No | No | Yes
File Services limits | 1 Standalone DFS root | 1 Standalone DFS root | Unlimited

**Other requirements:**

You also must have the following:

- Gigabit (10/100/1000baseT) Ethernet adapter
- DVD drive (if you intend to install the operating system from DVD media)

The following items are not strictly required, but are necessary for certain features:

- Super VGA (1024 x 768) or higher-resolution monitor
- Keyboard and Microsoft® mouse (or other compatible pointing device)
- Internet access (fees may apply)

>*Source: https://technet.microsoft.com/en-us/library/dn303418(v=ws.11).aspx*

<a name="gui"></a>
## GUI ON and OFF

### GUI Off with Powershell

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


### GUI On with Powershell

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

