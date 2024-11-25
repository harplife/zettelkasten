# GUI programming with Dear ImGui
## Dear ImGui
- Github - https://github.com/ocornut/imgui
- <mark class="hltr-trippy">Dear ImGui</mark> is a bloat-free GUI library for C++, which was designed to enable fast iterations and to empower programmers to create content creation tools and visualization / debug tools (as opposed to UI for the average end-user).
	- It favors simplicity and productivity toward this goal and lacks certain features commonly found in more high-level libraries (such as full internationalization and accessibility features).
	- It is particularly suited to integration in game engines (for tooling), real-time 3D applications, fullscreen applications, embedded applications, or any applications on console platforms where OS features are non-standard.
- Dear ImGui uses immediate mode, which 

## Immediate mode vs. retained mode
### Immediate mode
- In <mark class="hltr-trippy">immediate mode</mark>, the user interface is rebuilt and re-rendered every frame based on the current state of the application.
	- Meaning, the UI logic is often tightly integrated with the rendering loop, making it highly dynamic and responsive.
- Key characteristics:
	- **Stateless rendering** : the application itself is responsible for maintaining the state of UI components.
	- **Declarative updates** : UI elements are drawn every frame, and interactions (e.g. button presses) are handled immediately.
	- **Code-driven UI** : UI construction and event handling are explicitly defined in code.
- Advantages:
	- Simple to integrate with game engines or render loops.
	- Highly dynamic and flexible, making it ideal for real-time applications like games and visualization tools.
	- No need for complex data structures to store the UI hierarchy.
- Disadvantages:
	- Can be less efficient because UI is recomputed every frame.
	- Managing state is more manual and can lead to increased complexity for large applications.
- Libraries that uses immediate mode:
	- Dear ImGui

#### Immediate mode in game development
- Immediate mode based GUI libraries are useful for specialized use cases such as:
	- In-game debug overlays
	- Level editors embedded within the game
	- Diagnostic tools and performance profilers
- It can be easier to add more tools in the game engine directly using IMGUI, as opposed to adding tools to a game development software (e.g. unreal engine).

#### In-engine debug tool
- An in-engine (in-game) debug tool is a utility integrated directly into a game engine to monitor, diagnose, and modify the game or its systems during development.
	- These tools offer several advantages, especially in game development, where rapid iteration and real-time debugging are essential.
- Real-time debugging
	- **Immediate feedback** : changes or diagnostics can be applied and observed while the game is running, helping devs spot and fix issues without restarting.
	- **Dynamic analysis** : devs can monitor frame rates, memory usage, physics behaviors, AI states, and other metrics as the game runs.
- Faster iteration cycles
	- Rapid prototyping : devs can tweak variables (e.g. player speed, gravity, or lighting) on the fly, which accelerates experimentation and balancing.
	- Reduced downtime : avoiding recompilation or restarting the application saves significant development time.
- Improved efficiency for debugging complex systems
	- **Access to game state** : devs can inspect or modify internal states like object positions, physics forces, or AI behaviors directly in the running game.
	- **Custom breakpoints** : debug tools can pause the game at specific states or events to allow detailed inspection.
- In-game visualization
	- **Draw debug lines** : visualize physics collisions, AI navigation paths, or object hierarchies directly within the game environment.
	- **Overlay information** : display frame rates, input diagnostics, and performance metrics directly on-screen.
- Streamlined team collaboration
	- **Accessible for non-programmers** : designers and artists can use the debug tools to adjust gameplay parameters or test assets without needing deep coding knowledge.
	- **Shared debug information** : team members can identify and report issues more effectively with consistent in-engine debugging tools.
- Enhanced profiling and performance monitoring
	- **Frame timing and memory usage** : tools like frame graphs and memory allocators help identify bottlenecks.
	- **Real-time data** : profiling tools provide a clear picture of how various systems interact under load.
- Customization and extendibility
	- **Game-specific tools** : debug tools can be customized to meet the unique requirements of a specific game or project, such as visualizing AI states or network traffic.
	- **Extendable frameworks** : tools integrated into the engine can evolve with the game, ensuring continuous utility throughout development.
- Seamless deployment across platforms
	- Debug tools in an engine are often designed to work across multiple target platforms, enabling testing on different devices.

### Retained mode
- In <mark class="hltr-trippy">retained mode</mark>, the UI components are stored in a hierarchical structures (a "scene graph" or similar data structure) that persists across frames.
	- Updates to the UI are made by modifying the structure, and the system takes care of rendering it.
- Key characteristics:
	- **Stateful rendering** : the framework manages the state and hierarchy of UI components.
	- **Event-driven updates** : only changes to the UI structure trigger re-renders.
	- **Abstraction** : UI logic is often abstracted away from rendering.
- Advantages:
	- Efficient rendering since only updates are re-rendered.
	- Easier to create complex, hierarchical UIs.
	- Built-in support for common UI elements and features like layouts, animations, and accessibility.
- Disadvantages:
	- More abstract and less flexible compared to immediate mode.
	- Can have higher overhead in terms of memory and performance for simple applications.

#### Retaine mode in game development
- Retained mode GUI libraries are ideal for polished, static, and complex interfaces, such as game menus or editors.
	- However, they may not align well with the dynamic, real-time needs of in-game debugging or overlays.
	- Balancing immediate and retained mode libraries often provides the best of both worlds in game development.