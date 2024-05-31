In the context of the transformation pipeline typically used in computer graphics, especially with shaders in OpenGL or similar APIs, the spaces involved in the `projection * view * model` matrix multiplication are as follows:

1. **Model Matrix (Model to World Transformation):**
   - **Model Space:** This is the local coordinate space of an object. Coordinates of vertices are defined relative to the object's own origin.
   - **World Space:** The model matrix transforms vertices from model space to world space. This transformation places the object correctly in the scene, accounting for its position, rotation, and scale in the world.

2. **View Matrix (World to View Transformation):**
   - **World Space:** This is the coordinate space where all objects are placed in the scene. After applying the model matrix, vertices are in world space.
   - **View Space (Camera Space or Eye Space):** The view matrix transforms vertices from world space to view space. This transformation simulates the camera's position and orientation, effectively moving the entire scene so that the camera is at the origin looking down the negative z-axis.

3. **Projection Matrix (View to Clip Transformation):**
   - **View Space:** After applying the view matrix, vertices are in view space, where the camera is at the origin.
   - **Clip Space:** The projection matrix transforms vertices from view space to clip space. This transformation applies perspective (or orthographic) projection, mapping the 3D coordinates to a 2D plane while preserving depth information. Clip space coordinates are then used for further stages of the rendering pipeline, such as clipping and perspective division.

### Summary of Spaces:

1. **Model Space:** Local object coordinates.
2. **World Space:** Coordinates transformed by the model matrix, positioning the object in the scene.
3. **View Space:** Coordinates transformed by the view matrix, positioning the camera at the origin.
4. **Clip Space:** Coordinates transformed by the projection matrix, applying the perspective or orthographic projection.

### Transformation Sequence:

Given a vertex in model space, the transformation sequence can be written as:

\[ $\text{vertex}_{clip}$ = $\text{projection}$ $\times$ $\text{view}$ $\times$ $\text{model}$ $\times$ $\text{vertex}_{model}$ \]


Where:
- \($\text{vertex}_{model}$\) is the vertex position in model space.
- \($\text{model}$\) is the model matrix that transforms the vertex to world space.
- \($\text{view}$\) is the view matrix that transforms the vertex to view space.
- \($\text{projection}$\) is the projection matrix that transforms the vertex to clip space.

### Practical Example in GLSL:

Here's a typical vertex shader that demonstrates these transformations:

```glsl
#version 330 core

layout(location = 0) in vec3 inPosition;

uniform mat4 modelMatrix;
uniform mat4 viewMatrix;
uniform mat4 projectionMatrix;

void main() {
    vec4 worldPosition = modelMatrix * vec4(inPosition, 1.0);  // Model to World
    vec4 viewPosition = viewMatrix * worldPosition;            // World to View
    gl_Position = projectionMatrix * viewPosition;             // View to Clip
}
```

In this shader:
- `inPosition` is the vertex position in model space.
- `modelMatrix` transforms it to world space.
- `viewMatrix` transforms it from world space to view space.
- `projectionMatrix` transforms it from view space to clip space, resulting in `gl_Position`, which is used by the GPU for further processing and rendering.
