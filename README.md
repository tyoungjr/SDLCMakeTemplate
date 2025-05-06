# SDL2 CMake Template

An SDL2 CMake Template designed to streamline the development of SDL2-based projects. This repository provides a starting point for building C++ applications with SDL2 using CMake.

## Features

- **CMake Integration**: Simplifies the build process for SDL2 projects.
- **Cross-Platform**: Works seamlessly on Windows, macOS, and Linux.
- **Minimal Configuration**: Pre-configured to get started quickly.
- **Modular Design**: Easily extendable for larger SDL2 projects.

## Requirements

- **CMake** (version 3.15 or higher)
- **SDL2 Library**
- **A C++ Compiler** (e.g., GCC, Clang, MSVC)

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/tyoungjr/SDLCMakeTemplate.git
   ```

2. Navigate to the project directory:
   ```bash
   cd SDLCMakeTemplate
   ```

3. Create a build directory and configure the project:
   ```bash
   mkdir build && cd build
   cmake ..
   ```

4. Build the project:
   ```bash
   cmake --build .
   ```

5. Run the generated executable:
   ```bash
   ./YourExecutable
   ```

## File Structure

- `CMakeLists.txt`: Main CMake configuration file.
- `src/`: Source files for your SDL2 project.
- `include/`: Header files for your project.
- `assets/`: Resources like images, sounds, etc. (if applicable).
- `build/`: Directory for generated build files (not included in the repository).

## Contributing

Contributions are welcome! Please feel free to submit issues, fork the repository, and create pull requests.

## License

This project is licensed under the [MIT License](LICENSE).
