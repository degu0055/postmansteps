# Postman

In this project, we used Postman as the primary tool for working with the APIs. This tool serves as a bridge to communicate on different APIs, allowing users to perform the CRUD or Create, Update, and Delete. With the Postman interface, it makes working with the API easier as you can organize API requests into collections, automate testing, and work with the team.

Once you successfully register and log in to the account, the homepage will look like this:

![Homepage](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/1-homepage.png)

## Steps:

### **Create Workspace**
A workspace is a shared environment that enables teams to collaborate on API development, testing, and documentation.

![Workspace](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/workspace.gif)

### **Create Collection**
A collection is a set of related API requests designed for easy testing and sharing.

![Collection](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/collection.gif)

### **Perform Connection Test**
This will verify that the API is accessible and functioning correctly before proceeding with further testing.

![Connection Testing](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/Connection-Test.gif)

### **Configure OAuth2.0 Token**
An OAuth 2.0 token is a digital key that authenticates API requests, proving you have permission to access data or perform actions.

![Configure OAuth2.0 - 1](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/auth1.gif)

- Select ‘POST’ for request type.
- Click the Authorization tab.
- In the Auth type dropdown, choose OAuth 2.0.

### **Fill-up the Configure New Token Form**

![Configure OAuth2.0 - 2](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/auth2.gif)

| **Field**           | **Value**                                                                                           |
|---------------------|-----------------------------------------------------------------------------------------------------|
| Callback URL        | [https://www.getpostman.com/oauth2/callback](https://www.getpostman.com/oauth2/callback)             |
| Auth URL            | [https://login.microsoftonline.com/8e70bfc6-d0bb-41ef-920b-e02e1d7ac590/oauth2/v2.0/authorize](https://login.microsoftonline.com/8e70bfc6-d0bb-41ef-920b-e02e1d7ac590/oauth2/v2.0/authorize) |
| Access Token URL    | [https://login.microsoftonline.com/8e70bfc6-d0bb-41ef-920b-e02e1d7ac590/oauth2/v2.0/token](https://login.microsoftonline.com/8e70bfc6-d0bb-41ef-920b-e02e1d7ac590/oauth2/v2.0/token) |
| Client ID           | 38a0c582-fa83-4333-95a4-e530349652e2                                                                |
| Client Secret       | d3d3d3d3-d3d3-d3d3-d3d3-d3d3d3d3d3d3                                                           |
| Scope               | api://cst8911-restapi/Group.Read.All                                                                |

### **Use the token**

![Configure OAuth2.0 - 3](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/auth3.gif)

- Click the button 'Get New Access Token'.
- Enter your email.
- Enter the OTP.
- Click the button 'Use Token'.

--- 

### **Making POST**

Now that we have gained the token, this means a **POST** request can be made on the object, allowing us to send data and perform actions securely

> [!IMPORTANT]
> All the REST API requires a default key for authentication and a JWT token for role control, unless otherwise specified in the documentation below.

### **Add Course List** 

![Add Course list](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/create.gif)

Code:

```json
{
  "courseList": [
    { "cst8911": "Introduction to Cloud Computing" },
    { "cst8916": "Remote Data" }
  ]
}
```

### **Add Assignment**

![Add Assignment](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/addAssignment.gif)

Code:

```json
{
    "courseId": "cst8911",
    "assignmentId": "Assignment1",
    "title": "First Assignment",
    "content": "Write a report on cloud computing trends"
}
```

### **Submit Assignment**
![Submit Assignment](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/submitAssignment.gif) 

Requirements:

- File = CST8916.pdf

- Meta:

```json
{
  "userId": "user123",
  "courseId": "cst8911",
  "assignmentId": "Assignment1"
}
```

---

### **GET Method**

The GET request is used to retrieve data from a server. It asks the server to send back information, like details from a website or a database. It's commonly used to fetch data without making any changes to the server.

![GET Course](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/getCourse.gif) 

To fetch user details for the `cst8911` course, use the following API request:

https://rest-api.azurewebsites.net/api/<mark>getUser?course=cst8911</mark>




