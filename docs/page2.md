# Getting Started

## Prerequisites
* `python`: 3.10 or above
* `conan`: 2.2.0 or above
* `llvm`: 17 or above
* `make`: CMake downloaded via conan to make our project
* `git`: (only needs to really be installed on Windows)

## Installing prerequisites

=== "Windows"

    It is recommended to using Choco for an easy installation for Windows.

    To install `choco`, open powershell with admin access abd run this following command in your terminal:
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```


    !!! tip
        If `choco` command does not work after running this script try closing and reopening powershell again.
        When `choco` prompts you to run install scripts from commands below, enter `all` so it could install everything.

        After installing MinGW, add C:\Users\<username>\ProgramData\chocolatey\bin to your environment variable path to make it available globally.
    
    Install `git` (powershell must be admin):
    ```powershell
    choco install git
    ```
    
    Install `mingw` (powershell must be admin):
    ```powershell
    choco install mingw
    ```
    
    Install `python` (powershell must be admin):
    ```powershell
    choco install --version=3.12.0
    ```
    
    Install `llvm` (powershell must be admin):
    ```powershell
    choco install llvm
    ```
    
    Install `conan` (powershell must be admin)
    ```powershell
    python -m pip install -U "conan>=2.2.2"
    ```

=== "MacOS X"

    Make sure homebrew is installed, if not installed run the following command below.
