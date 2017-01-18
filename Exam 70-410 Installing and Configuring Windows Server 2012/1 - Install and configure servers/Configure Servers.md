# Configure Servers

## Contents
- [OS Licensing and Server Versioning](#licensing)
- [Windows Server 2012 Limits](#windows-limits)
- [Installation Requirements](#installation-reqs)
- [Server GUI On and Off](#gui)

<a name="licensing"></a>
## OS Licensing and Server Versioning

#### Server 2012 is not available in 32-bit
- Data Center
- Standard
- Essentials (same functionality of standard and web version of Windows Server 2008)
- Foundations

#### Differences in Licensing are exposed by the number of users and physical/virtual instances each support.

| EDITION    | POSE INSTANCES   | VOSE INSTANCES   |
| ---------- | ---------------- | ---------------- |
| Datacenter | 1                | Unlimited        |
| Standard.  | 1                | 2                |
| Foundation | 1                | 0                |
| Essentials | 1 (POSE or VOSE) | 1 (POSE or VOSE) |

<a name="windows-limits"></a>
## Windows Server 2012 Limits

|                                       | Foundation            | Essentials            | Standard / Datacenter |
| ------------------------------------- | --------------------- | --------------------- | ----------------------|
| Processor Limit                       | 1                     | 2                     | 64                    |
| RAM                                   | 32GB                  | 64GB                  | 4TB                   |
| Max users                             | 15                    | 25                    | Unlimited             |
| Routing and Remote Access (RRAS)      | 50                    | 250                   | Unlimited             |
| Active Directory Services             | Root only             | Root only             | Full                  |
| Active Directory Certificate Services | CA Only               | CA Only               | Full                  |
| Hyper V / Server Core                 | No                    | No                    | Yes                   |
| File Services limits                  | 1 Standalone DFS root | 1 Standalone DFS root | Unlimited             |

<a name"installation-reqs"></a>
## Installation Requirements

#### Minimum Requirements
- 1.4 GHz 64-bit processor (no upgrade path from a 32-bit system)
- 512 MB RAM
- 32 GB available disk space (considered as the minimum)
- DVD drive (not normally a pre-requisite)
- Super VGA (1024 x 768) or higher resolution monitor
- Keyboard and mouse (or other compatible pointing device)
- Internet access

#### Supported Maximums

| Component          | WINDOWS SERVER 2012 | WINDOWS SERVER 2008 R2 |
| ------------------ | ------------------- | ---------------------- |
| Logical processors | 640                 | 256                    |
| RAM                | 4 terabytes         | 2 terabytes            |
| Failover           | 63                  | 16                     |

<a name="gui"></a>
## GUI ON and OFF

#### GUI Off with Powershell

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


#### GUI On with Powershell

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

> **Sources:**
> - https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx*
> - http://www.howtogeek.com/111967/how-to-turn-the-gui-off-and-on-in-windows-server-2012/*

