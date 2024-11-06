# Recommended books for building games using Data-Oriented Design
Here are some highly regarded books focused on building game engines with **data-oriented design** and efficient, parallelizable architectures. They cover principles that support high-performance game engine development, including how to structure data for cache efficiency and CPU-GPU coordination, which are core to data-oriented design.

## 1. **Game Engine Architecture** by Jason Gregory
   - **Description**: This comprehensive book covers the architecture of game engines with in-depth explanations of essential engine systems. While not solely focused on data-oriented design, it does explore fundamental concepts of memory management and performance optimization that are essential for DOD.
   - **Recommended For**: Beginners to intermediate developers; provides a broad foundation for game engine design.
   - **Edition**: Make sure to get the latest edition, as it includes updated information relevant to modern hardware.

## 2. **Programming Rust** by Jim Blandy, Jason Orendorff, and Leonora F. S. Tindall
   - **Description**: This book isn't specific to game development, but Rust's design encourages data-oriented principles due to its strong emphasis on memory safety and performance. Many DOD game engine developers are beginning to use Rust due to its close-to-the-metal efficiency and its suitability for ECS (Entity Component System) architectures.
   - **Recommended For**: Intermediate to advanced developers, especially those interested in DOD and exploring Rust for game engines.
   
## 3. **Data-Oriented Design** by Richard Fabian
   - **Description**: A definitive book on the DOD paradigm. Although it is not specifically about game engines, this book provides a strong theoretical foundation in data-oriented programming, helping readers learn how to think about data layout, cache efficiency, and memory management, which are all essential for game engines.
   - **Recommended For**: Developers with a foundational understanding of programming who want a deep dive into DOD.

## 4. **Game Programming Patterns** by Robert Nystrom
   - **Description**: This book covers a wide range of programming patterns that are practical for game development. It discusses various performance-oriented patterns, such as the Object Pool and Flyweight patterns, which are compatible with data-oriented design and essential for high-performance game engines.
   - **Recommended For**: Intermediate developers who want to understand practical, applicable patterns for game engines. Although not solely focused on DOD, many patterns align with DOD concepts.

## 5. **Entity Component System Game Programming** by Rouslan Kryuchkov
   - **Description**: This book focuses on building games using the Entity Component System (ECS) approach, which is a natural fit for data-oriented design. It covers how to implement an ECS from scratch, with detailed explanations of component and system architecture, data-driven entities, and optimization strategies.
   - **Recommended For**: Developers looking to learn ECS, a DOD-compatible architecture, and who want practical, step-by-step instructions for building it into a game engine.

## 6. **Real-Time Rendering** by Tomas Akenine-Möller, Eric Haines, and Naty Hoffman
   - **Description**: Although primarily focused on rendering, this book includes extensive information about optimizing data structures and processing for modern hardware, such as GPUs and multi-core CPUs. These concepts are essential for high-performance game engines that rely on data-oriented design principles.
   - **Recommended For**: Developers interested in optimizing the rendering pipeline and learning advanced performance techniques that support DOD.

## 7. **Computer Graphics Programming in OpenGL with C++** by V. Scott Gordon and John Clevenger
   - **Description**: This book combines theory with practical programming, focusing on OpenGL and modern rendering techniques, but it also covers data layout strategies that improve performance on GPU-driven graphics applications.
   - **Recommended For**: Developers interested in the rendering aspect of game engines, especially those looking to understand how DOD can improve performance in graphics-intensive systems.

---

## Additional Resources

- **GDC Talks on Data-Oriented Design**: The Game Developers Conference often features talks on DOD by industry experts like Mike Acton. These presentations are highly practical and focused on real-world applications in game engines.
- **Blogs and Articles**: Richard Fabian’s blog and writings on data-oriented design are also good supplements to these books.

This list should give you a well-rounded understanding of DOD principles and how they apply to game engine architecture, from general patterns to specific ECS and rendering optimizations.