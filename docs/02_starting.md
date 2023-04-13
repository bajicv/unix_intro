<script>
function openTab(evt, tabName) {
  var i, tabcontent, tablinks;
  tabcontent = document.getElementsByClassName("tabcontent");
  for (i = 0; i < tabcontent.length; i++) {
    tabcontent[i].style.display = "none";
  }
  tablinks = document.getElementsByClassName("tablinks");
  for (i = 0; i < tablinks.length; i++) {
    tablinks[i].className = tablinks[i].className.replace(" active", "");
  }
  document.getElementById(tabName).style.display = "block";
  evt.currentTarget.className += " active";
}
</script>

<style>
.tab {
  overflow: hidden;
  border: 1px solid #ccc;
  background-color: #f1f1f1;
}

.tab button {
  background-color: inherit;
  float: left;
  border: none;
  outline: none;
  cursor: pointer;
  padding: 14px 16px;
  transition: 0.3s;
}

.tab button:hover {
  background-color: #ddd;
}

.tab button.active {
  background-color: #ccc;
}

.tabcontent {
  display: none;
  padding: 6px 12px;
  border: 1px solid #ccc;
  border-top: none;
}
</style>

# Starting OS native terminal

An operating system's native terminal is a command-line interface (CLI) provided by the operating system itself, allowing users to interact with the system using text-based commands. The native terminal provides a powerful and efficient way to manage files, run scripts, and execute commands on your computer, and is often preferred by advanced users and developers over graphical user interfaces (GUIs) due to its flexibility and customization options.

<div class="tab">
  <button class="tablinks" onclick="openTab(event, 'tab1')">Windows</button>
  <button class="tablinks" onclick="openTab(event, 'tab2')">Mac</button>
  <button class="tablinks" onclick="openTab(event, 'tab3')">Linux</button>
</div>

<div id="tab1" class="tabcontent">
  <p>Unfortunately, Windows comes with <b>Command prompt</b> or <b>Windows PowerShell</b> which is not of interest for us. However, there are many possibilities for us who have Windows OS to use Unix like terminal (e.g. Tabby, MobaXterm, Ubuntu on Windows 10, Babun, Putty Manager, Cygwin, and many others)! For this tutorial we will use <b>Tabby</b>.</p>
</div>

<div id="tab2" class="tabcontent">
  <p>The Mac command-line is a program called <b>Terminal</b>. It is located in the <b>/Applications/Utilities/</b> folder. To find it, go to your <b>Applications</b> folder. Near the bottom, you should find a folder called <b>Utilities</b>. Go inside, and one of the applications listed is called <b>Terminal</b>. Double-click that application to open it.</p>
</div>

<div id="tab3" class="tabcontent">
  <p>To find it, click on <b>Applications</b> and search for <b>Terminal</b> or <b>Konsole</b>. Go ahead and open the <b>command-line</b>. When you open it you will see a new window, with a simple <b>prompt</b> which indicates that the shell is ready for the input.</p>
</div>

------------------------------------------------------------------------

## Connecting to a remote server using OS native terminal

We will do most of our exercises on the remote computers (physically located outside of your homes :)) using the `evop-login.imp.fu-berlin.de` server. We can access them through the terminal (or terminal emulator). For the sake of testing the capabilities of your OS's native terminals (Windows, Mac, or Linux), we will execute the following command in your OS's native terminal.

So, let's do it! First, we have to open the terminal and then we have to type:

```
ssh -J YourID@andorra.imp.fu-berlin.de YourID@evop-login
```

[SSH](https://wiki.gentoo.org/wiki/SSH) (**S**ecure **SH**ell) is the ubiquitous tool for logging into and working on remote machines securely. All sensitive information is strongly encrypted, and in addition to the remote shell, SSH supports file transfer, and port forwarding for arbitrary protocols, allowing secure access to remote services. 

Two `ssh` options important for us are: 

- `-J` which allows us to jump through a host (from host1 to host2, in our case from `andorra` to `evop-login`). 

- `-X` which allows us to execute **graphical** applications remotely. Runing graphical applications remotely is very demanding for the network, so by default, we will NOT use this option during this tutorial. 

In addition to the main `ssh` command, the SSH suite of programs includes tools such as:

* `scp` - Secure Copy Program (which we will be using), 
* `sftp` - Secure File Transfer Protocol, or 
* `ssh-agent` to help with key management.

------------------------------------------------------------------------