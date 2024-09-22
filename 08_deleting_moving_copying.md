# rm command

1. The `rm` command is used to delete files and folders.

    ```bash
        rm App.js # permanently deletes App.js

    ```

2. **Deleting empty directories:** In order to remove an empty directory, we can either use the `rmdir` command or we can use the `rm` command with the `-d` or `--dir` option. If the directory to be deleted is not empty, then these commands would not work and throw a `directory not empty` error.

    ```bash
        # Suppose we have an empty directory named dogs and we want to delete it.
        rmdir dogs/
        rm -d dogs/
    ```

3. **Deleting non-empty directories:** In case a directory is not empty and we want to delete it, we can then use the `rm` command with the `-r` option. This stands for the recursive deletion of the files and folders present inside the directory. Note that we should not use this command carelessly as file once deleted is gone forever.

    ```bash
        # Suppose we have a directory to be deleted named Horses which is not empty.
        rm -r Horses/
    ```

4. **Interactive Deletion:** If we want that the process of deletion be interactive(ask for permission before each deletion), then we can use the `rm` command with the `-i` option.

    ```bash
        rm -r -i Horses/
    ```


## mv command

1. The `mv` command is used to move a file from one location to another location. We specify the source of the file and then the destination.

    ```bash
        # moves a.txt from the current wd to the parent of the cwd
        mv a.txt ../

        # moves b.txt present in the dogs folder of the cwd to the cats folder of the cwd
        mv dogs/b.txt cats/

        # moves kitty.txt present in the cats folder of the user abhishek to the dead_cats folder present inside the user abhishek (This is independent of the cwd as we are using the absolute paths)
        mv /home/abhishek/cats/kitty.txt /home/abhishek/dead_cats/
    ```

2. We can also use the `mv` command to rename the files.

    ```bash
        # renames the a.txt present in the cwd to b.txt in the cwd
        mv a.txt b.txt

        # moves a.txt present inside the dogs folder of the cwd to the cats folder of the cwd and renames it to b.txt
        mv dogs/a.txt cats/b.txt

    ```

3. We can also move multiple files using the `mv` command.

    ```bash
        # moves the a.txt b.txt c.txt present inside the cwd to the Notes folder inside the cwd
        mv a.txt b.txt c.txt Notes/

        # moves the scooby.txt (present inside the Dogs folder of the cwd) and skii.txt (present inside the Cats folder of the cwd) to the Dead folder (present inside the cwd)
        mv Dogs/scooby.txt Cats/skii.txt Dead/
    ```

4. We can also move folders using the `mv` command. However, if the destination directory does not exist, it would just rename the source directory after moving.

    ```bash
        # moves the Cats folder present inside the cwd into the Cleanup folder present inside the cwd
        mv Cats/ Cleanup/

        # In the above example, if the Cleanup directory does not exist, then Cats directorty would be renamed to Cleanup directory.
    ```

5. We can also move multiple folders using the `mv` command.

    ```bash
        # moves the Cats folder (present inside the cwd) and the dead_dogs folder (present inside the Dogs folder of the cwd) to the Cleanup folder (present inside the cwd)
        mv Cats/ Dogs/dead_dogs/ Cleanup/
    ```

## cp command

1. The `cp` command is used to copy a file or a folder from one location to other. We need to specify a destination folder or file. However, we can have multiple source files.

    ```bash
        # copies the todos.txt with the name moreTodos.txt
        cp todos.txt moreTodos.txt

        # copying multiple files
        cp 1.txt 2.txt 3.mp4 Cleanup/
    ```

2. The `cp` command can also be used to copy directories, however, in this case we need to use it with the option `-r` or `--recursive` which stands for recursive.

    ```bash
        # If Cleanup exists then a copy of Paralles would be made inside Cleanup. Otherwise, a new folder named Cleanup would be created which would be a copy of Parallels.
        cp Parallels/ Cleanup/ -r
    ```


# Assignment

Before we can delete, move, or copy things...we need things! It's time to get some more practice using `touch` and `mkdir`

Please create a new directory somewhere on your machine called `Bootcamp`.  Inside of it, create the the folders and files indicated below:

```bash
Bootcamp/
	FallCohort/
		Italo.txt
		Edgar.txt
		Linus.txt
		Sara.txt 
		Silvio.txt
		Waitlist/
			Hanna.txt
			Haris.txt
			Netta.txt
	WinterCohort/
		Santiago.txt
		Iris.txt
		Naomi.txt
```

- Sadly `Edgar` had to drop out of the course.  Delete the `Edgar.txt` file in `FallCohort`
- This means we now have space in our Fall Cohort to move someone off of the waitlist.  Please move `Netta.txt` from the `Waitlist` folder into the `FallCohort` folder.
- Please delete the `Waitlist` folder and its contents
- It turns out that I misspelled Sara.  She spells her name "Sarah" with an "h" at the end.  Please rename the `Sara.txt` file to `Sarah.txt`
- Unfortunately Italo is having a bit of a personal emergency, and he would like to move to our WinterCohort.  Please move the `Italo.txt` file from `FallCohort` to the `WinterCohort` folder
- Oh no, our entire Winter Cohort had to be cancelled because of a worldwide pandemic :(   We decided to bump all of the scheduled winter students to spring. In the `Bootcamp` directory create a copy of the `WinterCohort` folder called `SpringCohort`
- Please rename the WinterCohort folder to `WinterCohortCANCELLED`
- Oh no! We're going out of business. Please delete the entire `Bootcamp` directory 😢


# Assignment Solution 

```bash
cd ~
mkdir Bootcamp/FallCohort/Waitlist/ Bootcamp/WinterCohort/ --parents

cd Bootcamp/FallCohort/

touch Italo.txt Edgar.txt Linus.txt Sara.txt Silvio.txt

cd ../Waitlist/

touch Hanna.txt Haris.txt Netta.txt

cd ../../WinterCohort/

touch Santiago.txt Iris.txt Naomi.txt

cd ../..

# Delete Edgar.txt
rm Bootcamp/FallCohort/Edgar.txt

# Netta.txt move to FallCohort
mv Bootcamp/Waitlist/Netta.txt Bootcamp/FallCohort/

# Delete the Waitlist folder and its content
rm -r BootCamp/Waitlist/

# Sara.txt to Sarah.txt
mv Bootcamp/FallCohort/Sara.txt Bootcamp/FallCohort/Sarah.txt

# Italo.txt from FallCohort to WinterCohort
mv Bootcamp/FallCohort/Italo.txt Bootcamp/WinterCohort/

# copy of WinterCohort with the name SpringCohort
cp Bootcamp/WinterCohort/ Bootcamp/SpringCohort/ --recursive

# rename WinterCohort to WinterCohortCANCELLED
cp Bootcamp/WinterCohort/ Bootcamp/WinterCohortCANCELLED/ --recursive

# delete bootcamp
rm -r Bootcamp
```