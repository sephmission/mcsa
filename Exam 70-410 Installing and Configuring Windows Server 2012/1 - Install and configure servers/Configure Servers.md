# Configure Servers

### Licensing for Windows Server 2012 R2

#### Datacenter

Datacenter edition is ideal for customers who want to have a highly virtualized private and hybrid cloud environment. As always, it provides access to all the product features and enables unlimited instances of Windows Server with each license, enabling your virtual environment to grow as you do. The licensing for Datacenter edition will continue to be processor plus CAL (Client Access License), with each license covering up to two physical processors on a single server.

#### Standard

Standard edition is ideal for those customers who want to have a physical or lightly virtualized environment. This edition enables you to run up to two virtual instances of Windows Server with each license and provides all the same features as Datacenter edition. The licensing for Standard edition will continue to be processor plus CAL, with each license covering up to two physical processors on a single server, just like Datacenter edition.

#### Essentials

Essentials edition is ideal for small businesses that have up to 25 users and want to have a simpler, pre-configured connection to cloud-based services. This edition enables you to run a single virtual instance of Essentials. The licensing for Essentials will continue to be a server license for a two processor server that does not require CALs.

#### Foundation

Foundation edition is ideal for small businesses that have up to 15 users and want a general purpose server. The licensing for Foundation has not changed; it continues to be a server license for a one-processor server that does not require CALs and is sold only through OEM (original equipment manufacturer).

----

>*Source: https://www.microsoft.com/en-us/licensing/product-licensing/windows-server-2012-r2.aspx*


### System Requirements

| Description | Minimum Requirements     |
| ----------- | ------------------------ |
| RAM         | 512MB                    |
| Processor   | 1.4 GHz 64-bit processor |
| Disk space  | 32GB                     |

**Other requirements:**

You also must have the following:

- Gigabit (10/100/1000baseT) Ethernet adapter
- DVD drive (if you intend to install the operating system from DVD media)

The following items are not strictly required, but are necessary for certain features:

- Super VGA (1024 x 768) or higher-resolution monitor
- Keyboard and Microsoft® mouse (or other compatible pointing device)
- Internet access (fees may apply)

----
> *Source: https://technet.microsoft.com/en-us/library/dn303418(v=ws.11).aspx*


### GUI ON and OFF

#### **GUI Off with Powershell**

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

#### GUI On with Powershell**

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

