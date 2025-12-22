# Jelka FMF

Programmable Christmas tree at the Faculty of Mathematics and Physics, University of Ljubljana.

## About

At the [Faculty of Mathematics and Physics, University of Ljubljana](https://www.fmf.uni-lj.si/), as
part of the [FMF Programming Club](https://programerski-klub-fmf.github.io/), we set up a programmable
Christmas tree. The project was made possible with the sponsorship of [Abelium](https://abelium.si/)
and [Acex](https://acex.si/).

The tree is located at the entrance of the building at [Jadranska 21](https://www.google.si/maps/place/Jadranska+ulica+21,+1000+Ljubljana)
and is lit from morning until the building closes.

The main project website is available at [jelka.fmf.uni-lj.si](https://jelka.fmf.uni-lj.si/), and
the visual pattern editor is available at [jelkly.fmf.uni-lj.si](https://jelkly.fmf.uni-lj.si/).

## Contact

You can find contact information on the [project website](https://jelka.fmf.uni-lj.si/contact/).

## How It Works

Our tree consists of multiple components that work together to create a programmable Christmas tree.
The tree itself is controlled by a Raspberry Pi, which continuously communicates with the main server
to get the list of patterns to run. This program is called [Korenine](https://github.com/Jelka-FMF/Korenine).
It cycles through the available patterns and runs them one by one in a Docker container. The patterns
are containerized in the Docker container and can be written in any programming language that can write
to the standard output. The program reads the output of the pattern and controls the lights on the tree
accordingly using a library. The current state of the tree is also sent back to the server, where it
is displayed on the simulation on the website.

The main server, called [Jelkob](https://github.com/Jelka-FMF/Jelkob), hosts the project website, the
pattern database, and the Docker registry. The website is written in Django and uses the Django REST
framework for the API. Using the website, we can control which patterns are running on the tree and
manually run them. The website also shows a list of available patterns, the current state of the tree,
and the live simulation.

The patterns themselves are written in various programming languages and are stored in the
[Storži](https://github.com/Jelka-FMF/Storzi) repository. Each pattern is packaged in a Docker container.
The patterns can be written in any programming language that can write to the standard output, but we
provide user-friendly libraries for popular languages like Python and JavaScript. Patterns can read 3D
positions of the lights on the tree and control them accordingly by sending the desired colors to the
standard output.

To get the 3D positions of the lights on the tree, we recorded multiple videos of the tree from multiple
angles while running a calibration pattern. We then extracted a 2D position for each light for each angle.
Based on these 2D positions, we then calculated the 3D positions of the lights on the tree. This was done
using our program called [Jelkulator](https://github.com/Jelka-FMF/Jelkulator).

Another big part of the project is [Jelkly](https://github.com/Jelka-FMF/Jelkly), a Scratch-like visual
programming tool that allows users to create their own patterns without any programming knowledge. Jelkly
is written in TypeScript using the Microsoft's MakeCode (PXT) framework, which uses the Blockly library.
It provides the 2D and 3D simulation of the tree which enable users to see how their pattern would look
on the real tree. Patterns created in Jelkly can be directly submitted to the server, where we review
them, convert them to JavaScript, and add them to the Storži repository, where they can run on the tree. 

## Contributing Patterns

If you would like to contribute your own pattern for running on Jelka FMF and already have programming
knowledge, please check out the [Storži](https://github.com/Jelka-FMF/Storzi) repository that contains
already-existing patterns and instructions for submitting your own patterns in various programming
languages.

If you would like to submit a pattern but do not have programming knowledge yet, you can check out
[Jelkly](https://jelkly.fmf.uni-lj.si/docs), a Scratch-like visual programming tool for creating and
submitting your own Jelka FMF patterns. It is easy to use even for beginners and people without
programming knowledge, as it allows you to easily build programs using visual blocks. 

## Repository Organization

### Core

- **[Jelkob](https://github.com/Jelka-FMF/Jelkob)** - Main website for accessing and managing Jelka FMF
- **[Korenine](https://github.com/Jelka-FMF/Korenine)** - Rust system for running patterns on the Jelka FMF hardware
- **[Storži](https://github.com/Jelka-FMF/Storzi)** - Repository of patterns running on Jelka FMF

### Utilities

- **[Jelkly](https://github.com/Jelka-FMF/Jelkly)** - Blockly editor for creating and editing Jelka FMF patterns
- **[Jelkonda](https://github.com/Jelka-FMF/Jelkonda)** - A browser based development enviroment for reating and editing Jelka FMF patterns using Python
- **[JelkaSim](https://github.com/Jelka-FMF/JelkaSim)** - Simulation for running Jelka FMF patterns
- **[Jelkulator](https://github.com/Jelka-FMF/Jelkulator)** - Jupyter notebook for calculating light coordinates 

### Libraries

- **[JelkaPy](https://github.com/Jelka-FMF/JelkaPy)** - Python API for Jelka FMF patterns
- **[JelkaJS](https://github.com/Jelka-FMF/JelkaJS)** - JavaScript API for Jelka FMF patterns
