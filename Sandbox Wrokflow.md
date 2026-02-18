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

 # Project Playground
  - When the projectcreation api is resolved it returns the project id of the newly create project in the backend and redirects the user to /project/projectid route which is defined inside the Routing file 
  - For this route the ProjectPlayground component is rendered, Which is the parent component for other components.
  - ProjectPlaygroung project is responsible for rendering these component in this swquesnce:
  1. Treestructure (Alotement is not applicable as it is rendered conditionally)
  2. Editor component
  3. Browserterminal 
  4. Browser

# Editor Socket connection
 - When the project playground is first rendered it send a socket connection request to the backend for establishing a socket connection for Editor events. This connection is established using socket.io library on both backend and frontend
 - When the editor socket connection is established then this socket instance is stored in the editor socket store and project id is stored in the treeStructure store

# TreeStructure component
- It is rendered only when the projectId is present
- This component also has two components FileContextMenu and FolderContextMenu whch are to show the modal with the tree structure when any file or folder is Right Clicked.
- All the folders and files are rendered recursively using TreeNode component.
- 

 # Folder Structure 
 - When the project is created, the frontend recieve the project id in response and it renders the TreeStructure component which makes a request for project folder data using the treeStructureStore.
 - The entire folder structure is printed recursively using the data sent by the backend using a package directory tree

 # Editor Component
 - Editor component is rendered after the folder structure
 - The Editor uses LRU cache to implement the file tabs feature

 #

