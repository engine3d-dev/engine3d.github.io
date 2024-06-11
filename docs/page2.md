# 🛸 Getting Started

## ✅ Prerequisites

These are needed before working to get engine3d building successfully on your platform.

* `python`: 3.10 or above
* `conan`: 2.2.0 or above
* `llvm`: 17 or above
* `make`: CMake downloaded using conan to build Engine3D
* `git`: (only needs to be installed via installer on Windows)

=== "Windows"

    It is recommended to use Choco for an easy install for the Windows platform.
    
    To install `choco`, open powershell with admin access and run the following command in your terminal:
    
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
    
    !!! tip
    
        If `choco` command does not work after running this script try closing and reopening powershell again.
        When `choco` prompts you to run install scripts from the commands below, enter `all` so it can install everything.

        After installing MinGW, add `C:\Users\<username>\ProgramData\chocolatey\bin` to your environment variable path to make it available globally.
        Creating a copy in the `make.exe` and renaming it to `mingw32-make.exe` to get make working. If you do not do this, you will get the `CMAKE_MAKE_PROGRAM not set` error.
    
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
    
        If your using 20.04, you have to upgrade Python to 3.10
    
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

---

## Building Engine3D

Cloning the engine3d repository

!!! tip
    Add this flag at the end `-b missing` when conan cannot find packages in conan's cache.
    This means to build our packages and install any missing packages that we might have
    
* `conan create` command will install all the dependencies of engine3d and will build the project.

* `conan build .` will build the entire project

```bash
git clone https://github.com/engine3d-dev/engine3d
cd engine3d/

conan create .

conan build .
```

## Running Editor

The editor executable will be in `build/clang-17-x86_64-23-release/Editor/Editor.exe`

You can simply run the editor just by doing `.\build/clang-17-x86_64-23-release/Editor/Editor.exe`

Depending on your current platform the editor executable will be in `./build/<arch-Release>/Editor/Editor.exe`

---

## Different Build Types
There are two different build types that you can build engine3d in, `Release` and `Debug`.

`Release` will be turning on optimization and making your code size.

`Debug` is much slower than `Release`. Not recommended because used for testing and enabling debugging information.

---


