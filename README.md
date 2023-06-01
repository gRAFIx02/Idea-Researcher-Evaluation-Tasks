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


## Python & Docker

Q2.1

Steps to create a Docker container for a Python-based application are:
- Create a folder where all the required codes and files will be kept.
- Create necessary **.py** files with required codes.
- Create a **Dockerfile** with no extensions.
- Include necessary information inside the **Dockerfile**.
- From the terminal, package the application using the command  ```docker build -t <image_name> .```. This will create a docker image.
- Run the docker image using the command ```docker run --name <container_name> <image-name>```. This will create the required docker container.

The information we would need to add to the **Dockerfile** are:
- Specify the base image for the docker image using the instruction ```FROM```.
- Install any required dependencies using the instruction ```RUN```.
- Copy any required files from the local system to the docker image using the instruction ```COPY```.
- Set the current working directory for the subsequent commands using the instruction ```WORKDIR```.
- Include the commands to run when the docker starts using the instruction ```CMD```.

Q2.1

We can use Docker Compose to manage multi-container Python applications in the following ways:
- Create a ```docker-compose.yml``` file to define the services. This should be placed in the root directory of the project. The services can be configurations, dependencies, database, etc.
- Specify the container configurations inside the ```docker-compose.yml```, for example: specifying the base image, port mappings, environment variables, API, etc.
- Define any dependencies and relationships. For example, if the application relies on any database for various actions, the relationship and dependencies with the database should be defined.
- If we have custome Docker image, we can build it using ```docker-compose build``` command. If we want to use a pre-built image, Docker compose will automatically pull the image while running the service.
- Start the services using ```docker-compose up``` command. All the services defined in the ```docker-compose.yml``` file will be started. Docker compose will start all the containers, and the services will be run on separate isolated networks.
- Once the Docker Compose is run, we can interact with the Python application.
- To stop and clean up the services, we use ```docker-compose down``` command.
