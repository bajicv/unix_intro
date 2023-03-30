# Welcome to Intoduction to UNIX comand-line

This tutorial is part of the Bioinformatics for Biologists course at FU-Berlin. The assumption is that you have access to `evop-login.imp.fu-berlin.de` where the data is stored. 

This tutorial is designed for a biologist who did not have contact with a command line. At the end of this two-day tutorial, you should get familiar with some of the basic commands which you might use daily if you end up being a bioinformatician ;)  

During the first day, we should cover some basics such as how do we start UNIX terminal, and how do we navigate, make, delete, move and access directories and files. We should also learn what are pipes, filters, wildcards regular expressions and how to use them.

During the second day, we will dive deeper into using the wildcards and regular expressions to find patterns in our files or to locate directories or files on our computers. We would then learn how to work with tabular files and how to extract useful information from them using `awk`. We would also learn how to deal with repetitive tasks using loops and how to make scripts that we can use later on or share with friends and colleagues. We will also learn how to change the privileges for files and directories and how to use screen manager.

----

# Testing tabs

<div class="tab">
  <button class="tablinks" onclick="openTab(event, 'tab1')">Tab 1</button>
  <button class="tablinks" onclick="openTab(event, 'tab2')">Tab 2</button>
  <button class="tablinks" onclick="openTab(event, 'tab3')">Tab 3</button>
</div>

<div id="tab1" class="tabcontent">
  <p>Content for tab 1 goes here.</p>
</div>

<div id="tab2" class="tabcontent">
  <p>Content for tab 2 goes here.</p>
</div>

<div id="tab3" class="tabcontent">
  <p>Content for tab 3 goes here.</p>
</div>

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

----