# Camera
- In the previous chapter, using the View Matrix to move around the scene was discussed. OpenGL itself is not familiar with the concept of a "camera", but as a developer, one can simulate a camera by moving all objects in the scene - giving the illusion that the camera itself is moving.
- In this chapter, setting up a fly style camera that can freely move around in a 3D scene will be discussed. Using keyboard and mouse input to move the camera will be discussed as well. The chapter will conclude by making a custom camera class.

## Camera/View Space
- When a Camera/View Space is discussed, it generally refers to all the Vertex Coordinates as seen from the Camera's perspective as the origin of the scene: the View Matrix transforms all the World Coordinates into View Coordinates that are relative to the Camera's position and direction.
- There are a few things that are needed to define a Camera:
	- Its position in World Space
	- The direction it's looking at
	- A vector pointing to the right and a vector pointing upwards from the camera
- ![[camera_axes.png]]
- All in all, a Camera's own coordinate system will be created with 3 perpendicular unit axes with the Camera's position as the origin.

### 1. Camera Position
- Previously, objects in the scene were pushed back to simulate a camera. This time a vector will be used to represent the Camera's position in World Space, like so:

```C++
glm::vec3 cameraPos = glm::vec3(0.0f, 0.0f, 3.0f);
```

### 2. Camera Direction
- Another vector is required to represent the Camera's direction. For now, the Camera will be set to look at the origin of the scene `(0,0,0)`.
- (personal note) the website "explains" a concept called a Direction Vector; but it does not make any sense.
- 