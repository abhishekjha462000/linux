# Navigating in linux systems

1. In linux, the starting point for the file system is the root folder. We call it the root, but its actual directory name is `/`.

2. Confusingly, there is also a sub directory named `root`, this is actually a folder in `/`.

3. We also have a `home` directory inside the `/` directory.  The `/home` contains a home folder for each of the user on our system.
    To navigate to this folder, we can just use `cd /home`.

    ```bash
        # changes to the home directory inside the / directory
        cd /home 

        # changes to the user with the name Abhishek inside the home directory
        cd /home/Abhishek 
    ```

4. We also have some variables like `/` which stands for the root of the FS. Similarily, we also have the variable  `~` which stands for the home directory of the current user. 

    ```bash
        # changes to the / (top level directory)
        cd / 

        # changes to the current user home directory
        cd ~

        # changes to the current folder
        cd .

        # changes to the parent directory of the current directory
        cd ..

    ```

5. The `pwd` command stands for `print working directory`. It prints the absolute path of the current directory in which we are working. This is a simple but very useful command. We can think of it as `where am i` command.

6. The `ls` command is used to list all the files and folders present in the current directory. However, we can also use for viewing the content of a folder which is not our current working directory. We may do so by using the absolute path of the directory the contents of which we want to view.
    ```bash
        
        # lists the contents of the current directory
        ls

        # lists the contents of user Priya
        # It does not matter where we are currently as we are using the absolute path.
        ls /home/priya 

        # lists all the contents of the dog folder present in the current working directory
        ls dog/

        # lists all the files and folders including the hidden ones
        ls -a
        ls --all

        # lists all the files and folders with their details (long listing format)
        ls -l

        # lists all the files and folders with details including the hidden ones
        ls -la
        ls -al
        ls -l --all

        # -h prints the sizes in human readable format. This only makes when we use -l
        ls -h # does not make sense
        ls -h -l

        # --sort=time sorts by the time of creation
        ls -la --sort=time

        # --sort=size (-S) sorts by the size
        ls -la --sort=size
        ls -la -S

        # lists all the contents of the parent directory in a long listing format including the hidden files and folders and then sorts them by size.
        ls .. -al --sort=size
    ```

7. The `cd` command is used to change the directory from the current working directory, "moving" into the other directory.

    ```bash
        # changes to the home directory of the current user
        cd ~ 

        # changes to the top level directory
        cd /

        # changes to the dogs folder present in the current working directory
        cd dogs/

        # changes to the parent of the current working directory
        cd ..

        # changes to the puppies folder inside the dogs folder in the current working directory
        cd dogs/puppies/

        # changes to kitties folder in the cats folder of the priya user
        cd /home/priya/cats/kitties/

        # changes to the peacocks folder in the animals folder present in the parent directory of the currrent working directory
        cd ../animals/peacocks/
    ```

8. We also have other folders like `bin/`. This folder contains the list of all the binaries present in a Linux system. The `etc/` folder contains a bunch of configuration files. We also have a `root` folder. We cannot move into the `root` folder as permission is denied.

    ```bash
        cd bin/

        cd etc/

        cd root/ # permission denied
        ls /root/ # permission denied
    ```