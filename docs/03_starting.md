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

# Starting terminal

## OS native terminal

An operating system's native terminal is a command-line interface (CLI) provided by the operating system itself, allowing users to interact with the system using text-based commands. The native terminal provides a powerful and efficient way to manage files, run scripts, and execute commands on your computer, and is often preferred by advanced users and developers over graphical user interfaces (GUIs) due to its flexibility and customization options.

### Opening OS native terminal

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

### Connecting to `evop-login` server using `ssh`

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

## Tabby

Considering that you are using different kinds of OS we will use the Tabby terminal app which runs on Windows, Mac, and Linux. This way everyone will be able to follow tutorials without much difficulty (hopefully). And tabby will make it easier for you to download and upload files from/to a remote server (pay attention to step 8 described below).

![](https://user-images.githubusercontent.com/161476/126016449-a053012a-e322-48ed-a2ab-3ed4f3281465.png)

[Tabby](https://tabby.sh/) is an infinitely customizable, free, cross-platform terminal app for local shells, serial, SSH, and Telnet connections. It runs on Windows, Mac, and Linux.

------------------------------------------------------------------------

### Installation

Follow [this YouTube tutorial for installing Tabby on Windows/Linux/MacOS](https://www.youtube.com/watch?v=G03-5RE0ohg&t=2s). You can also find short summary of the steps below.

<div class="tab">
  <button class="tablinks" onclick="openTab(event, 'tab4')">Windows</button>
  <button class="tablinks" onclick="openTab(event, 'tab5')">Mac</button>
  <button class="tablinks" onclick="openTab(event, 'tab6')">Linux</button>
</div>

<div id="tab4" class="tabcontent">
  <p>1. Go to <a href="https://github.com/Eugeny/tabby/releases/tag/v1.0.196">https://github.com/Eugeny/tabby/releases/tag/v1.0.196</a>. <br/> 
     2. Click on <b>tabby-1.0.196-setup-x64.exe</b>. <br/>
     3. Once <b>tabby-1.0.196-setup-x64.exe</b> is downloaded double-clicking on it and install it. <br/>
     4. To start the program search for app <b>Tabby Terminal</b>.</p>
</div>

<div id="tab5" class="tabcontent">
  <p>1. Go to <a href="https://github.com/Eugeny/tabby/releases/tag/v1.0.196">https://github.com/Eugeny/tabby/releases/tag/v1.0.196</a>. <br/>  
     2. Click on <b>tabby-1.0.196-macos-x64.pkg</b>. <br/>
     3. Once <b>tabby-1.0.196-macos-x64.pkg</b> is downloaded follow the installer. <br/>
     4. To start the program search for <b>Tabby</b> and open it.</p>
</div>

<div id="tab6" class="tabcontent">
  <p>1. Go to <a href="https://github.com/Eugeny/tabby/releases/tag/v1.0.196">https://github.com/Eugeny/tabby/releases/tag/v1.0.196</a>. <br/>   
     2. Click on <b>tabby-1.0.196-linux-x64.deb</b> to download it. <br/>
     3. Install it in command line by typing: <b>sudo dpkg -i tabby-1.0.196-linux-x64.deb</b>.<br/>
     4. To start the program type: <b>tabby</b> in command line and press enter.<br/><br/>
      If you still have problems try following these steps: <a href="https://linux.how2shout.com/how-to-install-tabby-terminal-on-ubuntu-22-04-linux/">How to install Tabby Terminal on Ubuntu 22.04 Linux</a>. </p>
</div>

------------------------------------------------------------------------

### Setting up `evop-login` connection in Tabby

Luckily Tabby allows us to save connections so we can easily access them.

<b>1</b> - Click on `Settings` in the upper right corner or in the middle panel.

![Step 1](pics/Tabby_Step_01.png)

<b>2</b> - Select `Profiles & connections` tab in the left side pane and click on `+ New profile` on the right side.

![Step 2](pics/Tabby_Step_02.png)

<b>3</b> - Select `SSH connection` from the dropdown menu.

![Step 3](pics/Tabby_Step_03.png)

<b>4</b> - Fill in the fields `Name: andorra`, `Host: andorra.imp.fu-berlin.de`, and `Username: your_ZEDAT_username`, and press `Save`.

![Step 4](pics/Tabby_Step_04.png)

<b>5</b> - Click on `+ New profile` and select `SSH connection`

![Step 5](pics/Tabby_Step_05.png)

<b>6</b> - Click on `Connection` and in the drop-down menu select `Jump host`. In the newly appeared field `Jump host` select `andorra`. Fill in the rest of the fields `Name: evop-login`, `Host: evop-login.imp.fu-berlin.de`, and `Username: your_ZEDAT_username`, and press `Save`.

![Step 6](pics/Tabby_Step_06.png)

<b>7</b> - Now press `Profiles & connections` tab and select the newly created connection `evop-login`, enter passord and you will be connected to `evop-login` server.

![Step 7](pics/Tabby_Step_07.png)

<b>8</b> - To allow Tabby's `SFTP` to open our working directory we need to add a line of code in our `.bashrc` file. <br/>
You can open it by typing: `nano ~/.bashrc`. <br/>
When in nano scroll to the very end and paste (or type): <br/>
`export PS1="$PS1\[\e]1337;CurrentDir="'$(pwd)\a\]'`. <br/>
Exit by pressing `Ctrl+X` and then type `Y` to save changes and press `Enter` to close the file.

<b>9</b> - Now when we open new tab with `evop-login` we will be able to see files and directories in our working directory when we click on `SFTP` located in upper right corner. This way we can easily download files from server to our local computers, and upload files from our local computers to evop-login server.

![Step 8](pics/Tabby_Step_08.png)

![Step 9](pics/Tabby_Step_09.png)


Now you are set up and we can start learning about the command line!

------------------------------------------------------------------------