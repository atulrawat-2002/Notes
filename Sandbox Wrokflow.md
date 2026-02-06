# The flow starts from create project page


# Creation Of the project

1. The button makes an api call to the backend to /api/v1/project/

2. In the backend the Project Router pass the control to the createProjectController inside controller folder

3. The createProjectController invokes the createProjectservice and gets the Project Id of newly created project

4. The createProjectservice first generate a unique project id using uuid package then it creates a new directory inside the 'projects' folder with the name of uniqu project id (./projects/projectId)
 - Then it executes the project creation command using 'exec' function of 'child process' module of nodejs
 - The exec function is promisified using the promisify function of utils module of nodejs
 - The REACT_PROJECT_COMMAND is defined in the environment variables of the project
 - REACT_PROJECT_COMMAND is executed inside newly created directory with project id name
 - 