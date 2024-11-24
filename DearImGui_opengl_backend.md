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

### Retained mode
- In <mark class="hltr-trippy">retained mode</mark>, the UI components are stored in a hierarchical structures (a "scene graph" or similar data structure) that persists across frames.
	- Updates to the UI are made by modifying the structure, and the system takes care of rendering it.
- Stateful rendering : the framework manages the state and hierarchy of UI components.
- Event-driven updates : only changes to the UI structure trigger re-renders.
- Abstraction : UI logic is often abstracted away from rendering.
- Advantages:
	- Efficient rendering since only updates are re-rendered.
	- Easier to create complex, hierarchical UIs.
	- Built-in support for common UI elements and features like layouts, animations, and accessibility.
- Disadvantages:
	- More abstract and less flexible compared to immediate mode.
	- Can have higher overhead in terms of memory and performance for simple applications.
	- 