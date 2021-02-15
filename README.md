# cmake-multiexec

#### About 

Template for CMake projects with dependencies and which are expected to generate one separate executable per C source file

- Useful for projects containing multiple distinct code examples

- Each C source file is expected to have an entry point

#### Usage

###### General

- Add/Clone libraries to `Resources` > `Libraries`
- Update libraries in `CMakeLists.txt` accordingly
- Update project name in `CMakeLists.txt`

###### Visual Studio

- Open a local folder
- `Project` > `Generate cache for <project-name>`
- Right click a source file in the `Solution Explorer` and `Set as Startup Item`
- Build with `Ctrl+B`
- Debug with `F5`
