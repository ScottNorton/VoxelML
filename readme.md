# VoxelML

**VoxelML** is a fully code-generated voxel engine built to push the boundaries of procedural content generation and interactivity. 

The engine is available as a development test at [VoxelML.com](https://voxelml.com).  
If you would like to support this, please post any issues you find.

---

## Features

- **100% Code-Generated Texture & Geometry**: As a rule, every aspect of the engine is generated through code, presenting huge challenges with sweet results. The engine uses `Math functions` that take 3D coordinates as input and return information about what exists at those positions.
- **Voxel-Based Geometry Engine**: The heart of VoxelML is its voxel engine, improved over years in several forms. More specifically it's a geometry generator, which creates objects out of very small 3D cubes, or "voxels," similar to how pixels work in 2D images. This engine not only generates these structures but also allows for real-time **deformation**—meaning objects in the scene can be modified, broken apart, or reshaped dynamically. In addition, the engine simulates some basic **physics**, so things like collisions and impacts can affect the environment; for example, an explosion might cause a crater to form or debris to scatter.
- **In-scene Interface**: The interface construction is not HTML in the page itself, instead the geometry for the interface rendered in a second layer over the perspective view. This makes it available and more predictable in several platforms and packages.
- **No Serialization For Big Data**: This is one of my favorite parts. Emscripten uses the same memory as JavaScript, so C# code doesn't need to do anything more than store the data generated in an addressable object, and JavaScript code can access it.
- **Web-Based Engine**: The engine is fully web-compatible on devices with a modern web browser and aims for full immersive VR support for use with physically interactive content creation and animation as a project goal.
  - **Client-Server Architecture** *(future)*: Optionally run a server to keep things connected with a TLS encrypted WebSocket client that talks to the state management server, tracking, validating, and flagging changes in real-time.
- **Machine Learning Integration** *(future)*: ML.NET integration is a key future objective, with some fun stuff like shape recognition and moderation happening on the server side. Pending further research as it's more complex than expected, but it's a pillar of this project and must be done. A few shotgun implementations will be seen over time.
- **That's Cool, But Where's the Sound?** *(future)*: I don't know. I'll think on it.

---

*VoxelML* - Created because it was a cool idea.
