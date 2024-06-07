# 🛸 Getting Started

## ✅ Prerequisites

These are needed before working to getting engine3d building successfully on your platform.

* `python`: 3.10 or above
* `conan`: 2.2.0 or above
* `llvm`: 17 or above
* `make`: CMake downloaded via conan to make our project
* `git`: (only needs to really be installed on Windows)

=== "Windows"

    It is recommended to using Choco for an easy installation for Windows.
    
    To install `choco`, open powershell with admin access abd run this following command in your terminal:
    
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
    
    !!! tip
    
        If `choco` command does not work after running this script try closing and reopening powershell again.
        When `choco` prompts you to run install scripts from commands below, enter `all` so it could install everything.

        After installing MinGW, add `C:\Users\<username>\ProgramData\chocolatey\bin` to your environment variable path to make it available globally.
        Creating a copy in the `make.exe` and renaming it to `mingw32-make.exe` to get make working. If you do not do this, you will get `CMAKE_MAKE_PROGRAM not set` error.
    
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
    choco install python --version=3.12.0
    ```
    
    Install `llvm` (powershell must be admin):
    
    ```powershell
    choco install llvm
    ```
    
    Install `conan` (powershell must be admin)
    ```powershell
    python -m pip install -U "conan>=2.2.2"
    ```
    
=== "Ubuntu"

    Install wget if it isn't already on your system
    `sudo apt-get install wget`

    Install the latest version of `llvm`
    
    ``` bash
    wget https://apt.llvm.org/llvm.sh
    chmod +x llvm.sh
    sudo ./llvm.sh
    ```
    
    !!! info
    
        If your using 20.04, you have to upgrade python to 3.10
    
    ``` bash
    sudo apt update
    sudo apt install software-properties-common -y
    sudo add-apt-repository ppa:deadsnakes/ppa
    sudo apt install Python3.10
    ```

    Installing Conan
    ``` bash
    python -m pip install -U "conan>=2.2.2"
    ```
---

## Setting up Conan

Setting up a conan profile for your specific platforms.

=== "Windows"

    If you are on an x86 architecture for Windows.
    
    ```powershell
    conan config install -sf profiles/x86_64/Windows/ -tf profiles https://engine3d-dev/conan-config.git
    ```

=== "X86 Linux"

    If you are on a linux platform that uses an x86 architecture.
    
    ```bash
    conan config install -sf profiles/x86_64/linux/ -tf profiles https://engine3d-dev/conan-config.git
    ```

## Building engine3d

Clone the engine3d repository. Here is the build process, using Conan.

Before building engine3d, you'll need to use the `conan create` command to install all the dependencies of engine3d and build the project.

!!! tip
    `-b missing` means to build our packages, and install any missing packages that we might have
    Simply doing `conan create .` on the first build should be fine.

```bash
conan create . -b missing
```

Once you have the step above has finished, continue with building engine3d.

To build you do the following step below using the conan command `conan build`.

``` bash
conan build .
```


## Different Build Types
There are two different build types that you can do for engine3d, `Release` and `Debug`.

`Release` is used when you want to build with the most optimizations enabled.

`Debug` would be used for enabling code that would be enabled for debugging purposes, and tends to be much slower than Release mode.




