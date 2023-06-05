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

## JavaScript 3D (Three.js)

Q3.1

The fundamental components required to render a basic 3D scene using Three.js are:
- A **renderer** is needed for rendering the 3D scene on the HTML canvas. It can be done using the function ```THREE.WebGLRenderer``` or ```THREE.CanvasRenderer```.
- A **scene** is required to hold all the objects that make up a scene. This can be done using the function ```THREE.scene```.
- A **camera** is required for the perspective and viewpoint from which the scene is viewed. There are multiple camera viewpoints, and depending on the requirement, one is chosen for the project.
- **Geometry** is required to define the type of object that we will be using in our scene. It can be a cube, sphere, cylinder, etc. These can be created using the function ```THREE.Geometry```.
- **Materials** define the texture, colour and other visual properties of a geometry, for example the diffused material, Phone material, Lambertian material, etc.
- A **mesh** is created by combining the geometry with the material. The mesh can be then used to perform transformations, like translation, scaling or rotation.
- **Lighting** is needed for getting a realistic 3D scene. There are various types of light, like point light, ambient light, directional light, etc. Depending on the requirement of the scene the light source is chosen.
- **Control** is an optional component, which is used when we want to include user interaction with the 3D scene. For example, letting the user view around a 3D car model by interacting with it.

Q3.2

In order to import and use a 3D model created in Blender in a Three.js application, we have to:
- Export the 3D model from Blender in **gltf** or **glb** format as Three.js works with 3D models in these formats.
- Add the file to the Three.js project folder and mention the path in the relevant part of the code.
- The model can be loaded using the **GLTFLoader** library from Three.js. If any necesaary transformations need to be done, they can be done after loading the model.
- If we want the model to loop forever, we need to create an update loop for the model by taking the difference of the starting and ending time from ```getDelta()``` function, and then passing the value inside the ```update()``` function as ```clock.getDelta()```.
- Finally, render the scene as usual.

## Blender, Python, JavaScript 3D and Docker

Q4.1

To create a pipeline for the given task, we can do the following things:
- **Generate 3D models** using Python scripts in Blender and then export the model in **glb** or **gltf** format.
```python
import bpy

#codes related to creating the 3D model
#...
#...

bpy.ops.export_scene.gltf(filepath='path/to/model.glb')
```

- **Set up a Flask application** which will serve as a web interface for displaying the 3D models generated by Blender using Python.

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    # Render the main template that displays the 3D model
    return render_template('index.html')

if __name__ == '__main__':
    app.run()
```

- At this stage, we can either integrate the Python script from Blender with Flask, or we can import the **gltf** or **glb** file in the ```index.html``` file of **Three.js** project file.

```js
<script>
//Set up scene
//Set up camera
//Set up renderer

//Load the 3D model
var loader = new THREE.GLTFLoader();
loader.load('/path_to_the_model.gltf', function(gltf)
{
  scene.add(gltf.scene);
}, undefined,
function(error)
{
  console.error(error);
});

//Render the scene
</script>
```

- Configure the **Docker environment** for the Flask application.

```python
# Specify the base image with Blender and Flask pre-installed
FROM blender/flask

# Copy the application code into the container
COPY . /app

# Set the working directory
WORKDIR /app

# Install any additional dependencies if required
#...

# Define the command to run the Flask application
CMD ["python", "app.py"]
```

- Finally, **build the Docker image** and run the Docker container.

```python
docker build -t myapp .
docker run -p 5000:5000 myapp
```

Q4.2

There can be a number of challenges and difficulties while developing this kind of application. Some of the challenges are given below:
- **Compatibility and Versioning**: Blender, Flask and Docker all have different versions and dependencies. Ensuring compatibility among these components can be a challenging task. For this, we have to make sure the components and their dependencies are compatible with one another before we start developing/ deploying the application.
- **Resource Consumption**: Generating 3D models can be a resource intensive task, especially for models with large number of polygons and more sophisticated rigging. In these case, we need to have a good hardware to make sure we get good performance, as well as try to write the Python scripts as efficiently as possible.
- **Networking and File Paths**: When running in a Docker container, networking and file paths can be different from the local development environment. We need to ensure that networking between the Flask application and Blender script works correctly, and handle file paths properly for accessing and exporting 3D models. Use relative file paths, mount volumes or use appropriate file-sharing mechanisms between the container and the host, and consider configuring network settings in the Docker environment.
- **Security**: This is a very important aspect as with any web application, security is the main concern. We need to develop the application such that it is not vulnerable to malicious attacks like injection, DOS, unauthorized access, etc. By regularly updating the dependencies and updating any security patches, this challenge can be overcome.
- **Scalability and Performance**: As the user base or the complexity of the 3D model grows, the scalability and performance of the application may become an issue. We need to monitor the performance, any scope of bottlenecks and other performance issues of the application as it keeps growing. We can implement caching mechanism, more optimized codes, asynchronous processing for time consuming tasks in order to overcome this issue.

## Docker & JavaScript 3D

Q5.1

To containerize a Node.js application serving a web-based 3D viewer powered by Three.js, we can do the following steps:
- **Create a Node.js application** that serves the web-based 3D viewer with required dependencies and configurations.
- **Prepare a Dockerfile** with required instructions for the Node.js application. A sample code is given below:
```python
# Specify the base image with Node.js pre-installed
FROM node:14

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json to the container
COPY package*.json ./

# Install the application dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Expose the port on which the application will listen
EXPOSE 5000

# Define the command to start the application
CMD ["npm", "start"]
```

- **Build the Docker image** using the command `docker build -t nodeapp .`.
- **Run the Docker container** with the command `docker run -p 5000:5000 nodeapp`. Thus, the Node.js application serving the web-based 3D viewer powered by Three.js will be running inside a Docker container which can be accessed from `http://localhost:5000`.

Q5.2

Considerations that I would need to keep in mind when deploying this Docker container in a production environment are:
- Using a **container orchestration tool** like Kubernetes or Docker Swarm to manage and scale the Docker containers. These tools help in load balancing, scaling and monitoring of the containers.
- **Security** is one of the most important concerns of a web-based application. We need to ensure the application is always updated with latest dependencies, patching any security holes as soon as possible and taking actions to block any kind of unauthorized or malicious attacks.
- As the web application grows, the number of user base may grow and the 3D models may get more complex. This can lead to **scalability and performance** issues. We need to keep in mind the resources we are using, and scale the resources such that the performance of the application remains good while the system doesn't get too complex or overloaded.
- Establish **continuous integration and deployment (CI/CD)** to automate the build, test and deployment process of the contenarized application.
- We should keep a **backup and disaster recovery** strategy in case of any major failure or data corrpution.


## Practical Task: Genetate a 3D Pyramid in Blender using Python

**Code:**
