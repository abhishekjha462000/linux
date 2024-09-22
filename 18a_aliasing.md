# Aliasing

In Linux, an alias is a shortcut or abbreviation for a command or a series of commands. It allows you to create a custom, often shorter, way to execute complex or frequently used commands. Aliases are particularly useful for saving time and avoiding repetitive typing.

```bash
    alias alias_name='command_to_run'
```

For example, to make ll a shortcut for ls -al (which lists files in long format with hidden files), you can do:

```bash
    alias ll='ls -al'
```


## some common aliases

```bash
    # Alias for listing files in long format with hidden files
    alias ll='ls -alF'

    # Alias for listing all files except . and ..
    alias la='ls -A'

    # Safe remove: rm with confirmation prompt
    alias rm='rm -i'

    # Safe copy: cp with confirmation prompt
    alias cp='cp -i'

    # Safe move: mv with confirmation prompt
    alias mv='mv -i'

    # Go up one directory
    alias ..='cd ..'

    # Go up two directories
    alias ...='cd ../..'

    # Clear the terminal screen
    alias cls='clear'

    # Grep with color for better visibility
    alias grep='grep --color=auto'

    # Disk usage in human-readable format
    alias df='df -h'

    # Directory usage in human-readable format
    alias du='du -h'

    # Update system (for Ubuntu/Debian)
    alias update='sudo apt update && sudo apt upgrade'

    # Search command history using grep
    alias histg='history | grep'

    # Python 3 shortcut
    alias py='python3'

    # Display memory usage in megabytes
    alias free='free -m'

    # Create directories including parent directories
    alias mkdir='mkdir -p'
```

## Making aliases permanent

To make an alias permanent, you need to add it to your shell’s configuration file (`.bashrc`, `.zshrc`, etc.), depending on the shell you use. For example, if you're using Bash, you can add the alias to `~/.bashrc`:

**Steps to Make Permanent Aliases**

1. **Open the shell configuration file:** For Bash:
    ```bash
        nano ~/.bashrc
    ```
2. **Add your aliases at the bottom of the file:** For example:
    ```bash
        # List all files in long format including hidden ones
        alias ll='ls -alF'

        # Go up one directory
        alias ..='cd ..'

        # Safe remove (with confirmation)
        alias rm='rm -i'

        # Grep with color output
        alias grep='grep --color=auto'
    ```
3. Save the file (Ctrl + O to save in nano, then press Enter, and Ctrl + X to exit).

4. Reload the `~/.bashrc` file to apply the changes immediately without restarting the terminal:

    ```bash
        source ~/.bashrc
    ```

## Listing all the aliases

In order to view all the aliases, we can use the `alias` command without any parameter.

```bash
    alias
```

This will list down all the aliases that are there.

## Removing an alias

We can remove an alias using the `unalias` command.

```bash
    unalias alias_name

    alias pig='echo oink'
    unalias pig
```