## touch command

1. The `touch` command is used to create an empty file. 

2. The `touch` command is called "touch" because its primary purpose is to "touch" a file by updating its timestamps (access and modification times) without actually modifying its contents. If the file does not exist, `touch` will create an empty file, which is another form of "touching" the file system.

3. The touch command does not care about the extension of the file. It just creates an empty file.

    ```bash
        touch rusty
        touch cats dogs horses

        touch audio.mp3 script.py aao_wish_kre.mp4
    ```

4. **File types and extensions**: The file extension in the name of the file does **not** determine its actual type. For example, if we change the extension of a mp4 file to mp3, it does not actually change the file to an mp3 file. The files internal type is still mp4. We can use the `file` command to know the internal type of a file. The `file` command uses 3 types of tests to determine the actual file type of the file: file-system tests, magic tests and language tests.

    ```bash

        # create the files with different extension
        touch a.mp4
        touch b.mp3
        touch c.py
        touch d.txt
        touch e.docx

        # all are empty types, does not matter the extension of the file
        file a.mp4 # empty
        file b.mp3 # empty
        file c.py # empty
        file d.txt # empty
        file e.docx # empty

        # an actual mp4 file
        file aao_wish_kre.mp4 # mp4

        # However, if we rename the above movie into mp3 and then use the file command, then still we will get mp4
        file aao_wish_kre.mp3 # mp4
    ```


## mkdir command

1. The `mkdir` command is used to make an empty directory. It can only create a single directory at a time.

    ```bash
        mkdir dogs # makes dogs inside the current working directory

        mkdir love/puppy # makes puppy directory only if love directory is present inside the current working directory. If not, then no folder with the name of puppy would be created.

        # If we want that parents directory also be created, then we may use the -p or --parents option.
        mkdir --parents cats/indian/ruby # This will create ruby folder along with all the parent directories inside the current working directory
    ```


## Assignment

Create the following folder and files structure using CLI.

```bash
    my-app/
        README.md
        package.json
        public/
            index.html
        src/
		    components/
			    Navbar/
            App.css
            App.js
            index.css
            index.js
```

## solution

```bash

    mkdir --parents my-app/public/ my-app/src/components/Navbar
    cd my-app/
    touch README.md package.json public/index.html
    cd src/
    touch App.cs App.js index.css index.js
    cd ../../
```