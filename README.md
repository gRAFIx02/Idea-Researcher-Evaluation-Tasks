# Idea-Researcher-Evaluation-Tasks
Evaluation tasks for the job of idea researcher.

# Technical Exam: Blender, Python, JavaScript 3D and Docker

## Blender & Python

Q1.1

In order to create a 3D model in Blender using Python scripting, we have to -
- Open the text editor in Blender.
- Rename and save the file (in .py format).
- Write the required code inside the text editor.
- Save and run the file.

### Example code snippet
```ruby
import bpy

#clear existing objects
bpy.ops.object.select_all(action = 'DESELECT')
bpy.ops.object.select_by_type(type = 'MESH')
bpy.ops.object.delete()

#create cube
bpy.ops.mesh.primitive_cube_add(size = 2, enter_editmode = False, align = 'WORLD')

#access the cube (get reference to the cube)
cube = bpy.context.active_object

#modify the cube's location
cube.location = (0, 0, 5)

#modify the cube's scale
cube.scale = (5, 2, 3)

#modify the cube rotation
cube.rotation_euler = (0.3, 0.5, 0.2)
```

### Output
![Screenshot 2023-05-27 155538](https://github.com/gRAFIx02/Idea-Researcher-Evaluation-Tasks/assets/71190713/344ecdd2-9252-44b4-8288-67451bebe717)

Q1.2

The `bpy` module is used for interacting with the Blender's functionality and data. It supports the entirety of the 3D pipeline, that is modeling,rigging, animation, simulation, rendering, etc. This module serves as a bridge between Python and Blender, allowing the user to control and manipulate various aspects of the 3D scene.

In order to manipulate the object transformation in a 3D scene, we first have to get control over the object using `bpy.context.active_object`. Then, we can apply required transformations on the object by calling the corresponding functions. The example code snippet in Q1.1 contains the transformation example as well, where we select the `cube` object and perform translation, scaling and rotation operations on it.
