<h1>Arch Linux Installation</h1>
<p>Installation Guide from Main(<a href="https://wiki.archlinux.org/index.php/installation_guide">archlinux.org</a>)</p>

<img src="https://user-images.githubusercontent.com/66734606/111668311-06501f80-8844-11eb-9641-dc28371070ca.png" width="700px" height="350px">

<b><h3>!!WARNING!! Make Sure that you have backuped you files!! I recommend to try first it with Virtualbox</h3><b>
<b><h3>Arch Linux Image Doesn't Support Secure Boot.You Have To Disble Secure Boot In BIOS Settings</h3></b>
<br><br>
You Can Download Installation Image at <a href="https://archlinux.org/download/">Here</a>(<a href="https://archlinux.org/download/">Arch Linux</a>).After Download,Make Bootable USB With <a href="https://www.balena.io/etcher/">BalenaEtcher</a> or use <code>dd bs=4M if=/path/to/archlinux.iso of=/dev/sdx status=progress && sync</code>
<br>
To Boot Into Live Medium,Select Boot Arch Linux (x86_64).<br>
<img src="https://user-images.githubusercontent.com/66734606/111672488-66e15b80-8848-11eb-9d46-0b2af5a7a58f.jpg" width="600px" height="300px">
<br>
After Checking Process,You Will Get Shell With Root Permission(auto login).To Check UEFI Mode,Run ls command like this.<br>
<code>ls /sys/firmware/efi/efivars</code><br>
