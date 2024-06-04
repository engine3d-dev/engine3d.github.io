# Docs

## Build and Running

### Visual Studio Code
Assuming that all prerequisites are already installed, proceeding to the following:
1. Clone the repository: `git clone https://github.com/sfsu-dev/engine3d`
2. Installing dependencies using conan: `conan install . --build=missing`
3. Running the build: `conan build .`
4. Your executable to run the basic program would be from Sandbox in `build/Release/Sandbox/Sandbox.exe`
  * If running with Visual Studio then make sure that is installed and run the build process
  * Once generated the solutions file, run that solutions file in Visual Studio.

## How Layers work in Engine3D
Creating a basic application requires an `engine3d::Layer` to render the scene(s) to our application. Where we have our single instance of an application that will be our actual runtime application state. Now the application will take in these layers, overlapping them to be able to develop more complex scenes in our engine. As the engine is a layered-based layout on the client side.

* Engine3D from the user-space perspective is layer-based, which means that you are going to have different layers as different endpoints of your game or application. Suppose looking at the following example below.
* What does layer-based mean? This means how we handle frames are by overlapping these layers in sequence to play each frames.
* The following example, shows that we have a `MainLayer` that acts as our game layer with a few overridden methods.

### Layer Methods
Let's take a look at these methods:

`BeginPlay()`: is our initialization function that handles our behaviors for how you initialize your world.
`EndPlay()`: handling cleanly closing our applications or handling any tasks cleanup that is needed at runtime, if needed.
`UpdateEvent(Event&)`: handles all of our events being polled from engine3d.
`UpdateLayer()`: handles updating our layer for each frame in our application
`UpdateUI()`: This function handles any UI handling users may want to do within their application.


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


