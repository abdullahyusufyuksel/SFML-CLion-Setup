 # SFML Setup within CLion

## Understanding how CLion Handles Compilation & Execution

If you have ever wrote a simple "Hello World!" program within CLion, you would know that you are able to compile and run your code with a single click of the run button. The reason why you are able to have that streamlined experience is due to CLion's use of a framework called CMake within their project creation templates. The reason why CLion is able to maintain that single-click run experience even when multiple files are made is due to the fact that it automatically integrates it into your CMakeLists.txt file. What the CMakeLists.txt file does is that it uses bulit-in commands of the CMake language to essentially detail what the project is and how it's made. This can range from indicating the name of the executable and indicating source files all the way to complex compilation/execution rules. This is great beacuse it makes it so that a project can have lots of versatility, as you can determine what files and libraries to use.

## Static Libraries vs Dynamic Libraries
As you already know, C++ is quite a vast language that comes with the standard libraries installed (ie. string, stdexcept, etc.), but withs this being said there are still so many things that you simply can't do without using external libraries (unless of course you want to go about reinventing the wheel). In fact, many larger projects developed in the industry can you use several external libraries (ie. OpenGL, OpenCV, SFML..), and as a project becomes larger and larger linking the libraries within the terminal each and everytime can become quite tedious and tiresome - this is where the CMake frameworks comes in. CMake provides functions that allow you to link libraries for when you are compiling and running your software. 

# SFML




## Installation


### Windows



### MacOS
Open terminal and type copy the following.
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
This is instaling homebrew which is an open-source software package management system that simplifies the installation of software.

![](images/brew.png)
it should look something like this
```
brew install sfml
```
This installs sfml through homebrew

## Setup

### Windows

### MacOS
Once installation is done, in your Minesweeper project, copy and paste this into your CMakeLists.txt file:
```
cmake_minimum_required(VERSION 3.2)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(<your project name here>)

## If you want to link SFML statically
# set(SFML_STATIC_LIBRARIES TRUE)

## In most cases better set in the CMake cache
# set(SFML_DIR "<sfml root prefix>/lib/cmake/SFML")

find_package(SFML 2.5 COMPONENTS graphics audio REQUIRED)
add_executable(Minesweeper main.cpp)
target_link_libraries(Minesweeper sfml-graphics sfml-audio)
```

And replace the < your project name here > in  the "project(< your project name here >)" part with the name of the project you made in CLion. The gator brackets shouldn't be there. It should look like project(Minesweeper).



## Running it
Here is a main.cpp you can use to test to see if it works, it is also on the repo if you want to get it there. 

``` c++
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(200, 200), "SFML works!");
    sf::CircleShape shape(100.f);
    shape.setFillColor(sf::Color::Green);

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear();
        window.draw(shape);
        window.display();
    }

    return 0;
}
```



