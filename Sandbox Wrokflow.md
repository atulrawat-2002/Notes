# The flow starts from creating project page


# Creation Of the project

1. The button inside create project page makes an api call to the backend to /api/v1/project/

2. In the backend the Project Router pass the control to the createProjectController inside controller folder

3. The createProjectController invokes the createProjectservice and gets the Project Id of newly created project

4. The createProjectservice first generate a unique project id using uuid package then it creates a new directory inside the 'projects' folder with the name of uniqu project id (./projects/projectId)
 - Then it executes the project creation command using 'exec' function of 'child process' module of nodejs
 - The exec function is promisified using the promisify function of utils module of nodejs
 - The REACT_PROJECT_COMMAND is defined in the environment variables of the project
 - REACT_PROJECT_COMMAND is executed inside newly created directory with project id name
 - When the project is created we update it's vite config for loading the HMR port from environment variables
 NOTE: The HMR port is not present at the time of creation of project, it is available when the container is created

 # Folder Structure 
 - When the project is created, the frontend recieve the project id in response and it renders the TreeStructure component which makes a request for project folder data using the treeStructureStore.
 - The entire folder structure is printed recursively using the data sent by the backend using a package directory tree

 # Editor Component
 - Editor component is rendered after the folder structure
 - The Editor uses LRU cache to implement the file tabs feature

 #

