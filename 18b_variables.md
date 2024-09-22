# Variables in linux

1. In Linux, variables are used to store data that can be accessed and manipulated throughout the shell session or script. There are two main types of variables in Linux: **environment variables** and **shell (local) variables**.

## shell variables in linux

Shell variables are variables defined and used within a shell session to store temporary data, such as strings, numbers, or paths. These variables help manage and manipulate information during the execution of shell commands or scripts.

**Key Characteristics of Shell Variables:**

1. **Local Scope:** Shell variables are local to the current shell session. They are not automatically availiable to the child processes.

2. **Non Persistent:** These variables exist only for the duration of the shell session. Once the shell is closed or we make a new child shell, the variables are lost unless explicitly saved or exported.

    ```bash

        # creating a shell variable
        num=34

        # accessing a shell variable
        echo $num

        # Shell variables are not inherited by child processes unless explicitly exported.
        bash # starts a new sub shell session
        echo $num # does not know what is num


        # Example 2
        my_var="Hello"
        bash # Start a new shell session
        echo $my_var  # Outputs nothing (variable not inherited)
    ```
In summary, shell variables are useful for temporarily storing information during the execution of commands or scripts, but they have limited scope and are not available to child processes unless exported.

## Environment variables

If we want to make a variable an environment variable, we can do so by using `export` keyword. This would make it persist across all the child processes.

```bash
    export name=Alaadin

    echo $name # outputs Alaadin

    # start a new child session
    bash

    echo $name # outputs Alaadin as environment variables are persistent across the child sessions
```
**Important Note:**

However, once we close the current terminal window, the above variables do not persistent in a freshly opened session.
If we want that they persist across the other sessions as well, we need to edit the `~./bashrc` file and make a variable using the `export` keyword in this file. This would make it consistent in all the sessions for this particular user.

**Making Environment Variables Persistent Across Sessions:**

To ensure an environment variable persists across terminal sessions, add it to the `~/.bashrc` file:

1. **Open the configuration file.**
    ```bash
    nano ~/.bashrc
    ```
2. **Add the `export` statement:**
    ```bash
    export VAR_NAME="Persistent Value"
    ```
3. **Save and exit the file, then reload it:**
    ```bash
    source ~/.bashrc
    ```