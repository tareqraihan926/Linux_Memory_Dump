<p align="justify">
<h2 align="center">Analysis of the Linux Memory Dump</h2>


<!--
## Group Details

Four analysts form the group. Each task has been divided among the members as follows:

    Member 1: Analysis of the Network Artifacts.
    Member 2: Analysis of the Kernel Artifacts.
    Member 3: Analysis of the File System.
    Member 4: Analysis of the Kernel Modules & Analysis of Processes.
-->

## Memory Acquisition and Profile Generation

In order to compare machine1. cw1_machine1Infected.dump with the original virtual
machine, we performed a memory acquisition process using AVML Linux tool.<br><br>
For the first step I used the following command to create a memory dump.

      $> zip $(lsb_release -i -s)_$(uname -r)_profile.zip module.dwarf /boot/System.map-$(uname -r)
      
Created Profile is Debian_4.19.0-18-amd64_profile.<br><br>
The following screenshot shows the outputs.

<p align="center">

<img src="https://github.com/tareqraihan926/Linux_Memory_Dump/blob/main/Screenshots/1.PNG" width="" height="">
</p>

We also created the profile for the sample. To acquire the profile we followed the steps
below:

Using the avml package Acquired the Clean Memory Dump from the Debian Linux.

      $ sudo ./avml Memory.dmp
      
<p align="center">

<img src="https://github.com/tareqraihan926/Linux_Memory_Dump/blob/main/Screenshots/2.PNG" width="" height="">
</p>

The following image contains the details of the memory dump and the profile:

<p align="center">

<img src="https://github.com/tareqraihan926/Linux_Memory_Dump/blob/main/Screenshots/3.PNG" width="" height="">
</p>

After the acquisition of the clean memory dump, we performed an analysis of the
process hierarchy. The following diagram shows the hierarchy of processes:

<p align="center">

<img src="https://github.com/tareqraihan926/Linux_Memory_Dump/blob/main/Screenshots/4.png" width="" height="">
</p>

From the document of the project assignment, we know that we have to analyze a
memory dump file and make a pre-report of how we analyze that dump file according
to the requirement of the document.

Here a piece of memory is given named cw1_machine1Infected.dump. It is an
infected memory dump file. From the document, we know that first, we have to identify
the operating system used on this dump file.

To analyze a memory dump file we will use a Linux tool called avml. One of the
greatest open source software tools for 32-bit and 64-bit platforms to analyze RAM is
Volatility. Linux, Windows, Mac, and Android analysis are all supported. It may beused with Windows, Linux, and Mac operating systems and is based on Python. It can
examine a variety of dump types, including raw dumps, crash dumps, VMware dumps
(.vmem), virtual box dumps, and more.. To analyze the file we first have to open the
dump file in volatility. The command used in kali Linux to open the dump file is:


      Volatility -f file_name.dump imageinfo
      
To identify the operating system profile used in any dump file in volatility we have to
use the following command:

      Volatility -f file_name.dump kdbgscan
      
From this , we can see that by using this command in volatility we can see the kernel
information and identify the operating system used in this memory dump.

As we are using Kali Linux tool volatility to analyze this memory dump file, we install
this kali Linux operating system in Oracle VM virtual box. So we can tell the virtual
machine fits for this memory is Oracle VM Virtual box.

From the document, we can see that we have to create a clean memory dump file and
compare that dump file with the infected memory dump file that was given to us.

To create clean memory we use a tool called AVML. This tool is used to analyze image
files and create a dump file. The steps we have to follow to create a clean memory dump
file:

<p align="center">

<img src="https://github.com/tareqraihan926/Linux_Memory_Dump/blob/main/Screenshots/2.PNG" width="" height="">
</p>

We have to give the clean memory file name on the Destination filename: the section
that we want to create.

After selecting the options, we have to capture the memory and wait for the process to
finish as shown below. We have to wait for the extraction to complete.

And after it has finished extracting the memory dump we get a message that the
acquisition has been completed successfully.

This finishes creating a clean memory.

Then we have to compare this clean memory with the infected memory that we were
given. Compare also with-

      1: Analysis of the Network Artifacts.
      2: Analysis of the Kernel Artifacts.
      3: Analysis of the File System.
      4: Analysis of the Kernel Modules.
      5: Analysis of Processes. Etc.
      
To compare we have to use the volatility tool and Autopsy tool. An autopsy is also an
image file analyzing tool. We have to compare the clean memory dump file with the
infected memory dump file using volatility and we have to find which parts in the
infected memory have been changed compared to the clean memory that we have
created using AVML and we also have to identify what those changes mean.

To do this in volatility we run the same command for both of the memory dump file on
two different windows and find out the changes between these two dump files.

With the volatility command, we have to analyze the processes for the two dump files
and find out the differences between them. We also have to analyze the kernel and
network for the two dump files and find out the differences between them.

With the volatility tool and Autopsy tool we have to detect the file systems for the two
memory files and find out the differences between the new clean memory file with the
infected dump file.

With the volatility and Autopsy tool, we have to find out what kind of incident
happened for both of the memory files and detect the intrusion that happened in the
infected dump file compared to the clean memory dump file.

After finding out the differences and changes made to the infected dump file we have
to write what those changes mean and what happened on the infected file compared to
the clean memory dump file.

Noticing the different processes we define the main goal of each of these processes and
we will focus the analysis on each of them:

- Process Apache2 (PID **): This process is a web service. It suggests that the system
might be used as a server; this will be analyzed during the network analysis.
- Different Bash Processes (PID ** and PID **): These processes are user processes,
this suggest that a user might be using the system. The whole bash history will be
analyzed in...
- Network Malicious Connections and traffics log Investigation.
- Using PID find out the Process that is related to established the remote connection
from the infected machine and compare with Clean Memory dump. Etc.

</p>
