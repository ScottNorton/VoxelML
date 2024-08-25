# VoxelML

**VoxelML** is a fully code-generated voxel engine built to push the boundaries of procedural content generation and interactivity. The project is a result of a life-long .NET programmer discovering WebAssembly, Emscripten, and the `System.Runtime.InteropServices.JavaScript` namespace in the .NET Framework.

The engine is available as a development test at [VoxelML.com](https://voxelml.com).  
If you would like to support this, please post any issues you find.

---

## Features

- **100% Code-Generated Geometry**: As a rule, every aspect of the engine is generated through code, presenting huge challenges with sweet results.
- **Voxel-Based Geometry Engine**: The heart of VoxelML is its voxel engine, improved over years in several forms. More specifically it's a geometry generator, which creates objects out of very small 3D cubes, or "voxels," similar to how pixels work in 2D images. This engine not only generates these structures but also allows for real-time **deformation**—meaning objects in the scene can be modified, broken apart, or reshaped dynamically. In addition, the engine simulates some basic **physics**, so things like collisions and impacts can affect the environment; for example, an explosion might cause a crater to form or debris to scatter.
- **In-scene Interface**: The interface is part of the rendered content making it available and predictable on all platforms.
- **No Serialization For Big Data**: VoxelML employs Emscripten for direct access to WebAssembly memory buffers which can be accessed with read/write access using JavaScript to get information from C# code.
- **Web-Based Engine**: The engine is fully web-compatible on devices with a modern web browser and aims for full immersive VR support for use with physically interactive content creation and animation as a project goal.
  - **Client-Server Architecture** *(future)*: Optionally run a server to keep things connected with a TLS encrypted WebSocket client that talks to the state management server, tracking, validating, and flagging changes in real-time.
- **Machine Learning Integration** *(future)*: ML.NET integration is a key future objective, with some fun stuff like shape recognition and moderation happening on the server side. Pending further research as it's more complex than expected, but it's a pillar of this project and must be done. A few shotgun implementations will be seen over time.
- **That's Cool, But Where's the Sound?** *(future)*: Don’t worry, sound effects will be generated at 16-bit quality, 48 times per second, packed into a tiny buffer. By using variadic algorithms (fancy talk for "winging it with some parameters"), we’ll create ‘close enough’ approximations of sound effects through the magic of math. Multiple algorithms will sync together in the same buffer, with a bit of interpolation to smooth things out.

---

## Technologies Used in the Project

### 1. **C# / .NET 8 WebAssembly (WASM)**

- **Language**: C# 12
- **Framework**: .NET 8
- **Key Features**:
  - `System.Runtime.InteropServices.JavaScript`: Enables communication between TypeScript (JavaScript) and C# code.
  - Running in WebAssembly, some memory management and runtime performance specific to WebAssembly are included.
  - A highly flexible and hot-patchable client architecture in WebAssembly (when not compiled ahead of time) using MSIL and Expression Trees.

### 2. **TypeScript**

- **Key Focus**:
  - Handles all frontend logic and UI/UX including localization and rendering.
  - Provides improved maintainability and readability over JavaScript.
  - Interacts with C# WASM code through JavaScript interop.
  - Types for methods exported from C# within WebAssembly are typed by a custom tool, for RAD.

### 3. **JavaScript Interop**

- **Interop Layer**: System.Runtime.InteropServices.JavaScript (part of .NET 8 & 9)
- **Purpose**:
  - Enables seamless data and function calls between TypeScript and C# WASM.
  - Facilitates bidirectional event handling across the two environments, avoiding use of strings for any performance-critical operations.

---

## Programming Design & Architecture

The architecture of VoxelML follows a **modular design** approach to ensure high performance and maintainability.

- **C# WebAssembly (WASM)** powers performance-heavy operations, keeping them as distant from the JavaScript rendering context as possible.
- **JavaScript** manages frontend logic and UI/UX interactions, relying on [**Three.js by MrDoob**](https://github.com/mrdoob/three.js) for 3D rendering. There are no plans to change this library in the near future, as it provides the flexibility and performance needed for now.
- A clear separation exists between **TypeScript** and **C# projects**, with well-defined interop points facilitating seamless communication.
- **Direct memory access** is achieved through Emscripten, allowing JavaScript to interact with the C# WebAssembly memory buffer directly, bypassing the need for serialization except for local storage and network operations.
- A **server solution** is planned, supporting the shape recognition part of the project and a public state of the scene which can be interacted with in a live environment with other users.

---

*VoxelML* - Created with passion by a dedicated .NET developer exploring new things.
