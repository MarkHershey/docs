# Subprocess Call in Python

## `subprocess.run()`

`subprocess.run()` is high-level and easy to use. It is the recommended way to run a command in Python.

For example, we want to grab the output of the command `ls -l`.

```python
import subprocess

completed_proc = subprocess.run(
    ["ls", "-l"],
    capture_output=True,
    text=True,
)
print(completed_proc.stdout)
```

!!! warning
    - `subprocess.run()` is only available >= Python 3.5.
    - `capture_output=True` and `text=True` are only available >= Python 3.7.

    If you use Python 3.6, you may use equivalent code:

    ```python
    completed_proc = subprocess.run(
        ["ls", "-l"],
        stdout=subprocess.PIPE,
        stderr=subprocess.PIPE,
        universal_newlines=True,
    )
    print(completed_proc.stdout)
    ```

    - `capture_output=True` is simply a shortcut to `stdout=subprocess.PIPE` + `stderr=subprocess.PIPE`.
    - `text=True` is an alias to `universal_newlines=True`.

`subprocess.run()` accepts the shell command as a list of arguments. But instead of spiting the command into a list manually, we can use the `shlex.split()` function instead.

```python
import shlex
import subprocess

completed_proc = subprocess.run(
    shlex.split("ls -l"),
    capture_output=True,
    text=True,
)
print(completed_proc.stdout)
```

Another way is to use the `shell=True` keyword argument. When `shell=True` is specified, the command will be executed in the system shell program, which is equivalent to executing the command in a shell terminal.

```python
import subprocess

completed_proc = subprocess.run(
    "ls -l",
    shell=True,
    capture_output=True,
    text=True,
)
print(completed_proc.stdout)
```

!!! note
    By specifying `shell=True`, you can also make use of shell features like:

    - filename wildcards: `rm tmp_*.txt`
    - environment variable expansion: `echo $USER`
    - home directory expansion: `cd ~`
    - pipes: `nvidia-smi | grep clock`

    Like this will run as expected:

    ```python
    subprocess.run("ls ~", shell=True)
    ```

    But this will cause an error:
    

    ```bash
    >>> subprocess.run(["ls", "~"])
    ls: ~: No such file or directory
    ```

    - This is because the program `ls` does not recognize `~` as a valid path, only the shell program does.


`subprocess.run()` is a blocking function. It will wait until the command finishes before returning. If you wish to execute a command in the background, you should use the `subprocess.Popen()` function instead.

## `subprocess.Popen()`