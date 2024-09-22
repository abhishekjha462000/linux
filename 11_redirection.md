# Redirection in Linux

1. In Linux, we have 3 standard streams. These are like communication channels between a computer program and its environment. These are : `Standard Input`, `Standard Output` and `Standard Error`.

2. The `standard output` is a place to which a program or command can send information. The information could go to a screen to be displayed, to a file, or even to a printer or other devices.

3. The `standard input` is where a program or command gets its unput information from. By default, the shell directs standard input from the keyboard. The input information could come from a keyboard, a file or even from another command.

4. **Redirecting standard output:** The `>` operator is used to redirect the standard output (stdout) of a command to a file or another destination, replacing its contents if the file already exists. The `>` operator overwrites the contents of the specified file if it already exists. If the file specified does not exist, `>` will create it.

    ```bash
        ncal -3 > calendar.txt

        sort colors.txt > sorted_colors.txt

        ncal -3hj > julian_three_months_non_highlighted.txt

        ls ~/var/bin > bins.txt

        less items.txt > new_items.txt

        echo "Hello, World!" > greeting.txt
    ```

5. **Appending to a file:** The `>>` operator is used to append the standard output (stdout) of a command to a file without overwriting the existing contents. Unlike the `>` operator, which overwrites the file, the `>>` operator appends the output to the end of the specified file. If the file doesn't exist, it creates a new file. If the file doesn't exist, `>>` will create the file and then append the output.

    ```bash
        # Appending Text to a File
        echo "Hello, World!" >> greetings.txt

        # Appending Command Output
        date >> log.txt

        # Appending the Results of a ls Command
        ls /etc >> dir_list.txt
        
        # Appending to a file in loop
        for i in {1..5}; do
            echo "Iteration $i" >> loop_output.txt
        done
    ```

6. **Redirecting standard input:** The `<` operator in Linux is used to redirect input to a command from a file, making the command read from the file instead of standard input (keyboard). The file specified must exist and contain valid data, or else the command will fail.

    ```bash
        # This command will read the contents of input.txt and display them. It behaves the same as cat input.txt.
        cat < input.txt

        # same as sort names.txt
        sort < names.txt
    ```

7. `cat` and many other commands are set up to accept filenames as arguments directly, but we can also redirect to standard input manually.

8. In Linux, we can use both `<` and `>` (or `>>`) simultaneously to redirect input from one file and output to another file. This is useful when you want to process the contents of one file and save the results to another file. We can process data from one file and then store the result in another file.

    ```bash
        # Reads from sorted.txt and then writes the sorted output to sorted.txt
        sort < unsorted.txt > sorted.txt

        #  Reads from input.txt and writes the word, line, and byte count from input.txt to wordcount.txt
        wc < input.txt > wordcount.txt
    ```
9. **Redirecting standard error:** The `2>` operator is used to redirect standard error (stderr) output to a file. By default, errors are displayed on the screen (stderr), but `2>` allows you to redirect them to a file or another location for logging or analysis. Like `>`, the `2>` operator overwrites the file if it already exists. If the file does not exist, it will be created. 

    ```bash
        ls non_existing_file 2> error_log.txt

        # redirection to /dev/null
        ls non_existing_file 2> /dev/null

        # using both stdout and stderr
        ls /dev > output.txt 2> error_log.txt
    ```

10. **Appending standard error**: The `2>>` operator is used to append standard error (stderr) output to a file. Unlike `2>`, which overwrites the file, `2>>` appends error messages to the file, preserving existing content. If the specified file does not exist, `2>>` will create the file and append the error messages to it.

    ```bash
        ls non_existing_file 2>> error_log.txt

        command >> output.txt 2>> error_log.txt

        command 2>> /dev/null

        ls /non_existent_dir > output.txt 2>> error_log.txt

        # Reads from unsorted.txt, The sorted output is written to sorted.txt, overwriting any existing content and any errors (e.g., if unsorted.txt does not exist) are appended to sort_errors.txt.
        sort < unsorted.txt > sorted.txt 2>> sort_errors.txt
    ```

11. **Numerical descriptors of streams:** The `0` stands for standard input, `1` stands for standard output and `2` stands for standard error. Thus, in place of `<`, we can also use `0<`. Similarily, for `>` we can use `1>` and for `>>`, we may use `1>>`.

11. **Standard output and standard error in the same file:** We can redirect both standard output and standard error to the same file using the `2>&1` operator. This means that any errors that occur will be redirected to the stream with the numerical descriptor `1`, which is standard output. Conversely, using `1>&2` means that any output we receive will be redirected to the location where standard error writes. This approach allows us to capture both outputs in a single destination for easier debugging and logging.

12. **Newer Fancier Syntax:** Newer versions of bash also support a fancier syntax for redirecting both standard output and standard error to the same file: the `&>` notation.

    ```bash
        # redirect
        ls /var/bin &> output.txt

        # append
        ls /var/bin &>> output.txt
    ```

# Redirection Assignment
# Redirection Exercise

Download the files for this exercise:

[Wildlife.zip](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5347afb9-a379-4ccc-a6a7-25da129f3ad0/Wildlife.zip)

Unzip the `Wildlife` folder and navigate to it via the command line. 

## Your Task

You are taking part in a wildlife survey in a remote portion of the Peruvian Amazon! This morning, three of your research assistants each went on transect walks where they recorded the individual species they observed.     Your (simple) job is to combine their findings into a new file that contains all the species that were observed!

1. Create a new file called `all-species.txt` that contains the combined contents of `angela-survey.txt`, `nico-survey.txt`, and `juan-survey.txt`.  Do this using a single command!
2. The problem with the `all-species.txt` file is that it contains duplicate entries!  Use a single command to sort the lines in alphabetical order, only sorting uniques, and send the output to a new file called `sorted-animals.txt`
3. Now, you go out for a nice morning stroll and stumble upon a large anaconda sunning itself on a log.  You should add this observation to the list of species!!
    1. Start by appending the current date to the end of the `sorted-animals.txt` file using a command (don't open the file manually!)
    2. Then append the text "Green Anaconda" to the end of `sorted-animals.txt`
4. Run the non-existent command `ughhh` and redirect any error messages so that they are **appended** to the sorted-animals.txt file.

# Assignment Solution

```bash
    # Create a new file called all-species.txt that contains the combined contents of angela-survey.txt, nico-survey.txt, and juan-survey.txt.  Do this using a single command!

    cat angela-survey.txt nico-survey.txt juan-survey.txt > all-species.txt

    # The problem with the all-species.txt file is that it contains duplicate entries!  Use a single command to sort the lines in alphabetical order, only sorting uniques, and send the output to a new file called sorted-animals.txt

    sort all-species.txt --unique > sorted-animals.txt

    # Now, you go out for a nice morning stroll and stumble upon a large anaconda sunning itself on a log.  You should add this observation to the list of species!!

    # a. Start by appending the current date to the end of the sorted-animals.txt file using a command (don't open the file manually!)

    date >> sorted-animals.txt

    # b. Then append the text "Green Anaconda" to the end of sorted-animals.txt

    cat "Green Anaconda" >> sorted-animals.txt

    # Run the non-existent command ughhh and redirect any error messages so that they are appended to the sorted-animals.txt file.
    ughhh 2> sorted-animals.txt
```