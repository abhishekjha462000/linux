## cat & less command

1. The `cat` command is used to concatenate the files and print to the console. When given with only 1 file name, it outputs the contents of the file to the console. When given more than 1 file name, it outputs the contents of each file 1 by 1.

    ```bash
        cat colors.txt # outputs the content of colors.txt

        cat list.txt colors.txt # outputs the content of list.txt and then the content of colors.txt
    ```
2. In cases of large files, the `cat` command prints the entire content to the terminal in one go which can cause the content to scroll quickly, and one may lose sight of the beginning. In such cases we can use the `less` command.

    ```bash
        less countries.txt

        less greatGatsby.txt
    ```


## cat vs less
| Feature                 | `cat` Command                                           | `less` Command                                       |
|-------------------------|--------------------------------------------------------|------------------------------------------------------|
| **Purpose**              | Concatenates and displays the content of files          | View and navigate through the content of files       |
| **Handling Large Files** | Displays the entire file at once, causing overflow      | Shows one screen at a time, allowing easy scrolling  |
| **Navigation**           | No navigation, entire output shown in one go           | Scroll up/down, search, and move efficiently         |
| **Memory Usage**         | Loads the entire file into memory                      | Loads file in chunks, more efficient for large files |
| **Search Functionality** | No search functionality                                | Search with `/`                                      |
| **Quit**                 | No need to quit, finishes when content is fully displayed | Press `q` to quit the viewer                         |
| **Use Case**             | Small files or quick concatenation                     | Large files requiring navigation and searching       |


## tac & rev command

1. The `rev` command is used to reverse the content of each of the file in horizontal manner.

2. The `tac` command is used to reverse the content of each of the file in vertical manner.
    ```bash
        # horizontally reverses f1.txt and then prints to the console and then does the same for f2.txt
        rev f1.txt f2.txt

        # vertically reverses f1.txt and then prints to the console and then does the same for f2.txt
        tac f1.txt f2.txt
    ```

## head & tail command

1. The `head` command is used to display the first few lines of a file. By default, it shows the first `10` lines of a file. 

2. We can customize the number of lines to be shown by using the `-n`  or `--lines`option and then passing in the number of lines as argument.
    ```bash
        # first 10 countries
        head countries.txt

        # first 3 countries
        head -n 3 countries.txt
        head -n3 countries.txt
        head --lines 3 countries.txt
        head -3 countries.txt
    ```

3. The `tail` command in Linux is used to display the last few lines of a file. By default, it shows the last `10` lines, but you can adjust it to show any number of lines or even bytes. We can customize the number of lines to be shown by using the `-n` or `--lines`option and passing the number of lines as argument.

    ```bash
        # last 10 countries
        tail countries.txt

        # last 89 countries
        tail -n 89 countries.txt
        tail --lines 89 countries.txt
        tail -89 countries.txt
    ```

4. **Tracking the system with the tail command:** The `tail` command can be used to track the changes made in a file. This can be done using the `-f` option. This can be used to track the changes made in the system which can be done by tracking the `syslog.1` file present inside the `/var/log` directory.

    ```bash
        tail -f colors.txt

        # Now if we modify the file colors.txt, then any change made in colors.txt would be shown on console for the file.

    ```

## wc command

1. The `wc` command is used to tell us the number of words, lines or bytes in a file. By default, it prints three numbers: `#lines`, `#words`, `#bytes`.

2. We can restrict the output of `wc` using the `-l` (# lines) or `-w` (# words) options.

    ```bash
        # counts #lines, #words and #bytes
        wc countries.txt

        # counts #lines only
        wc -l countries.txt

        # counts #words only
        wc -w countries.txt
    ```

3. The `wc` command is often used while piping. For example, how many file names start with `sys` etc.

## sort command

1. The `sort` command is used to print the sorted contents of a file. It does not modify the original file.

2. **Reverse Sort:** In order to sort a file in the reverse order, we can use the `--reverse` or `-r` option. This prints the sorted file after reversing it vertically.

3. **Unique Sort:** Sometimes a file may contain duplicate entries, In such cases we can use the unique sort. This could be achieved by using the `-u` or `--unique` command.

4. **Numeric Sort:** The usual sorting order is lexicographical. This means that a number which starts with 1 (even 100_000) would be considered smaller than a number which starts with 4 (like 40). Due to this anomaly, we cannot perform numeric sort. To perform numeric sort, we can use the `-n` or `--numeric-sort` option.