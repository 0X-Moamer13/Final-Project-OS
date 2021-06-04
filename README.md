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
    
    ![Screenshot from 2021-06-04 09-48-22](https://user-images.githubusercontent.com/77538165/120837131-d2b39600-c512-11eb-8200-5550652e5736.png)


Now i will create a makefile      "nano Moamer/Makefile" 

And write "obj-y := Moamer.c" 


![Screenshot from 2021-06-04 07-37-16](https://user-images.githubusercontent.com/77538165/120832656-5ec2bf00-c50d-11eb-99be-a057b85b31f3.png) 
]

And i will open the Makefile to add the home directory to my  system call to the main Makefile of the kernel.
 
 
Open the Makefile with the following command.

"nano Makefile" and i will search for core-y it will apper in the second time of searching . We did the search to see this  "kernel/ certs/ mm/ fs/ ipc/ security/ crypto/ block/" 
I will add my home directory called Moamer . 



And I will open the header file with the following command.

""nano include/linux/syscalls.h""

 to add a corresponding function prototype for my system call to the header file of system calls.

Search for endif and put "asmlinkage long sys_Moamer(void);" above it . 


![Screenshot from 2021-06-04 07-43-40](https://user-images.githubusercontent.com/77538165/120833899-cf1e1000-c50e-11eb-9a61-35a5c5faca42.png) 

Add my system call to the kernel's system call table. By using "nano arch/x86/entry/syscalls/syscall_64.tbl" command  Note: Um 64bit if u 32bit just put 32 instead of 64. 

 I will navigate to the bottom of it even  find a series of x32 system calls.  I will put 
 
 "440     common  Moamer                sys_Moamer"  "above the section 32 "
 
 Now Installition: 
 
 I will install the new kernel and prepare your operating system to boot into it.


First : Configure the kernel.   use "make menuconfig" 

Use Tab to move between options. Make no changes to keep it in default settings.  

And  find out how many logical cores you have. in my machine um using 2 

Compile the kernel's source code. : by "make -j2" 


![Screenshot from 2021-06-04 07-52-06](https://user-images.githubusercontent.com/77538165/120834672-cf6adb00-c50f-11eb-9f23-f992649f7177.png) 


Prepare the installer of the kernel.By using  "sudo make modules_install -j2"

And Install the kernel. 


![Screenshot from 2021-06-04 08-03-49](https://user-images.githubusercontent.com/77538165/120834798-fe814c80-c50f-11eb-8d81-49f45457ae99.png)



Update the bootloader of the operating system with the new kernel. by using "sudo update-grub"


Now : I will  reboot my computer.


The result: 

First i will change my working directory to my home directory. 


Now i will Create a C file to generate a report of the success or failure of your system call.

using nano moamer.c and put this program :  

    #include <linux/kernel.h>
    #include <sys/syscall.h>
    #include <stdio.h>
    #include <unistd.h>
    #include <string.h>
    #include <errno.h>

    #define __NR_identity 440

    long identity_syscall(void)
    {
        return syscall(__NR_identity);
    }

    int main(int argc, char *argv[])
    {
        long activity;
        activity = identity_syscall();

        if(activity < 0)
        {
            perror("Sorry Try again .");
        }

        else
        {
            printf("Congrats The system call added\n");
        }

        return 0;
    }
 
 
 ![Screenshot from 2021-06-04 08-17-32](https://user-images.githubusercontent.com/77538165/120835218-810a0c00-c510-11eb-8149-4ab50b8a399e.png) 
 
 Now compile the program by usin **gcc** 
 

**gcc -o moamer moamer.c**



Run and you see 


![Screenshot from 2021-06-04 08-25-26](https://user-images.githubusercontent.com/77538165/120835720-291fd500-c511-11eb-9a45-5019a24c99a3.png)






 
 





 
 


 


