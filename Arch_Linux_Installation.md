<h1>Arch Linux Installation (Need Internet Connection)</h1>
<p>Installation Guide from Main(<a href="https://wiki.archlinux.org/index.php/installation_guide">archlinux.org</a>)</p>

<img src="archlinux.png" width="700px" height="350px">

<b><h3>!!WARNING!! Make Sure that you have backuped you files!! I recommend to try first it with Virtualbox</h3></b>
<b><h3>Arch Linux Image Doesn't Support Secure Boot.You Have To Disble Secure Boot In BIOS Settings</h3></b>
<br><br>
You Can Download Installation Image at <a href="https://archlinux.org/download/">Here</a>(<a href="https://archlinux.org/download/">Arch Linux</a>).After Download,Make Bootable USB With <a href="https://www.balena.io/etcher/">BalenaEtcher</a> or use <code>dd bs=4M if=/path/to/archlinux.iso of=/dev/sdx status=progress && sync</code>
<br><br><br>
To Boot Into Live Medium,Select Boot Arch Linux (x86_64).<br>
<img src="1-2.jpg" width="600px" height="300px">
<br>
After Checking Process,You Will Get Shell With Root Permission(auto login).To Check UEFI Mode,Run ls command like this.<br>
<code>ls /sys/firmware/efi/efivars</code><br>
If This Command Has No Error,Your System Has Enabled UEFI Mode.Some Steps Are Different For UEFI and Legacy.<br>
<br><br>
<b>Connect To The Internet</b><br>
I recommend Ethernet Connection.For Connecting Wifi(if wireless card is available),<br>
<code>$ iwctl device list<br>
$ iwctl station DEVICE scan<br>
$ iwctl station DEVICE get-networks<br>
$ iwctl --passphrase=PASSPHRASE station DEVICE connect SSID</code>
<br><br>
<b>Partition The Disk</b><br>
To list all disk and partitions,use <br>
<code>fdisk -l</code><br>
You Will Get Labelled /dev/sda or /dev/sdb./dev/sda is more common.So, To Partition the disk
<code>fdisk /dev/sda</code><br>
Must Create ESP Partition For UEFI System.(UEFI Only)If Not,Can Skip This Step.<br>
Type <i>m</i> for help.
To Create New Partition, Enter <i>n</i>.Select Partition Number.Hit Enter First Sector.Enter <i>+512M</i> in Last Sector.<br>
<br><br>
<img src="fdisk1.png" width="500px" height="110px">
<br><br>
To Change Parition Type, Enter <i>t</i>.And Enter L to list all parition types.Enter Number of EFI Parition Type<br>
<img src="efi_system_partition.jpg">
<br><br>
<b>Create Root Partition <u>(For Both UEFI and Legacy Systems)</u></b><br>
In the <code>fdisk</code> Command,Enter Partition Number,First Sector.
And I Enter The Reset of HDD for Last Sector <b>+10G</b><br>
After All Of This,Enter w To Write Changes On Disks.
<br><br>
<img src="root.jpg">
<br>
<i><h5>Summary for Partition:</h5>For UEFI System,We Need EFI Partition and Root Partition.<br>For Legacy System,We Only Need Root Partition.</i>
<br><br>
<b>Create File System</b><br>
Use <code>mkfs</code>command:<br>
<h5>For UEFI System</h5>
<code>mkfs.fat -F32 /dev/sda1</code> (For EFI Partition)<br>
<code>mkfs.ext4 /dev/sda2</code> (For Root Partition)
<br>
<h5>For Legacy System</h5>
<code>mkfs.ext4 /dev/sda1</code> (For Only One Partition {Root})<br>
