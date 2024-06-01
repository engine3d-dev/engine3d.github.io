# Getting Started

## Prerequisites
* `python`: 3.10 or above
* `conan`: 2.2.0 or above
* `llvm`: 17 or above
* `make`: CMake downloaded via conan to make our project
* `git`: (only needs to really be installed on Windows)

## Installing prerequisites

=== "Windows"

    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
    
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

## Quick Example
Creating a basic application requires to be a `engine3d::Layer` to render scene(s) to our application. Where we have our single instance of an application that will be our actual runtime application state. Now the application will take in these layers, overlapping them to being able to develop more complex scenes in our engine. As the engine is a layered-base layout on the client-side.

```c++ title="Application.cpp"

#include <engine3d/core/Layer.h>

namespace engine3d{
    class MainLayer : public Layer{
        void BeginPlay() override {}

        void EndPlayer() override {}

        void UpdateEvent(Event& event) override {}

        void UpdateLayer() override {}

        void UpdateUI() override {}
    };


    class ClientApplication : public engine3d::BlankApplicationSlate {
    public:
        ClientApplication(){
            this->PushLayer(new MainLayer());
        }
    };
};
```
