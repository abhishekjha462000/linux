# piping

1. Piping in Linux allows you to pass the output of one command as the input to another command. It’s a powerful feature of Unix-like operating systems that helps in creating complex workflows by chaining simple commands together. It redirects the standard output of a command to the standard input of the other command. For piping commands, we use the `|` operator.

    ```bash

        # count the number of files and folders in the cwd
        ls | wc -l

        # sorts the file colors.txt and then shows the top 10 results
        cat colors.txt | sort | head -n 10
    ```

2. **Important Distinction:** The `>` command is used to redirect the standard output of a command to a file. The `|` (pipe operator) is used to connect the standard output of a command to the standard input of another command. We can use these commands in conjuction, but it is important to remember that these are different things.

    ```bash
        # sorts the unsorted.txt and then overwrites it to the file with name sorted.txt
        cat unsorted.txt | sort > sorted.txt

        # counts the number of files and folders in the cwd and saves this in the file_count.txt file.
        ls | wc -l > file_count.txt

        # count the number of processes which have python in it
        ps aux | grep -i "python" | wc --lines
    ```
