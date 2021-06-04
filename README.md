**# Final-Project-OS 

First I will show the settings of my Virtual Machine : 

Number of cores: 2 

The capacity of memory is 2G 

The kernal virsion is 5.8.1 

Second: 


Steps to how to add a system call :  

1-Make my Linux ubunto up to date by 

" sudo apt-get update && apt-get update"   

2- Install all packeges that i will use to compile Kernal by : 

"sudo apt install build-essential libncurses-dev libssl-dev libelf-dev bison flex -y" 

3-UM using nano text editor  

Now Lets Go to do it :) 

 Now I will download the source code of the latest stable version of the Linux kernel (which is 5.8.1 as of 12 August 2020) And add i will add to my folder .


"wget -P ~/ https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.8.1.tar.xz" And unpack it by using "tar -xvf ~/linux-5.8.1.tar.xz -C ~/"



Now i will change to root and go on "linux-5.8.1".

Make a directory called Moamer  and create file called Moamer.c 
in this file write a program 

      #include <linux/kernel.h>
      #include <linux/syscalls.h>

      SYSCALL_DEFINE0(identity)

      {
    printk("I am Jihan Jasper Al-rashid.\n");
    return 0;
    }

Now i will create a makefile      "nano Moamer/Makefile" 

And write "obj-y := Moamer.c" 


![Screenshot from 2021-06-04 07-37-16](https://user-images.githubusercontent.com/77538165/120832656-5ec2bf00-c50d-11eb-99be-a057b85b31f3.png) 
]

And i will open the Makefile to add the home directory to my  system call to the main Makefile of the kernel.
 
 
Open the Makefile with the following command.

nano Makefile





