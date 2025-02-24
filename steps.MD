# Postman

In this project, we used Postman as the primary tool for working with the APIs. This tool serves as a bridge to communicate on different APIs, allowing users to perform the CRUD or Create, Update, and Delete. With the Postman interface, it makes working with the API easier as you can organize API requests into collections, automate testing, and work with the team.

Once you successfully register and log in to the account, the homepage will look like this:

![Homepage](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/1-homepage.png)

## Steps:

### **Create Workspace**
A workspace is a shared environment that enables teams to collaborate on API development, testing, and documentation.

![Workspace](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/workspace.gif)

1. **Workspaces** tab
2. Click **Create Workspace**
3. Select workspace type
4. Name your workspace

### **Create Collection**
A collection is a set of related API requests designed for easy testing and sharing.

![Collection](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/collection.gif)

1. Click **+**
2. Blank Collection
3. Name your Collection

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

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `addUser` to it.

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

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `addAssignment` to it.

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

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `submitAssignment?code=[code here]` to it.

Enter:

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

### Fetch user details using the `cst8911` course

![GET Course](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/getCourse.gif) 

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `getUser?course=cst8911` to it.

Result:
```json
    {
        "id": "5e99a784-5544-483f-8613-05100212c1a7",
        "name": "Zee Lu",
        "email": "zeel981210@gmail.com",
        "roles": [
            "Student"
        ]
    }
```

### Fetch user details using the `email`

![GET Email](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/getEmail.gif) 

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `getUser?email=youremail@gmail.com` to it.

Result:
```json
    {
        "id": "3549d894-e8df-4a94-8010-6cfa6bb6ba4a",
        "name": "Zee Lu",
        "email": "zeel981210@gmail.com",
        "roles": [
            "Student"
        ],
        "courseList": [
            {
                "cst8911": "Introduction to Cloud Computing"
            },
            {
                "cst8916": "Remote Data"
            }
        ]
    }
```

### Fetch user details using the `id`

![GET Email](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/getID.gif) 

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `getUser?id=yourID` to it.

Result:
```json
    {
        "id": "5e99a784-5544-483f-8613-05100212c1a7",
        "name": "Zee Lu",
        "email": "zeel981210@gmail.com",
        "roles": [
            "Student"
        ]
    }
```

### Fetch assignments details using the `courseId` and `assignmentId`

![GET Assignment](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/getAssignment.gif) 

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `getAssignments?courseId=cst8911&assignmentId=Assignment1` to it.

Result:
```json
    {
        "id": "65855dd8-9bf3-4ba7-bcdc-7f324aaa6a48",
        "userId": "user123",
        "fileName": "CST8916.pdf",
        "submissionDate": "2025-02-17T00:21:37.507Z",
        "downloadUrl": "https://cst8911storage.blob.core.windows.net/cst8911/cst8911/Assignment1/user123/CST8916.pdf"
    }
```

### Fetch assignments list using the `courseId`

![GET Assignment List](https://raw.githubusercontent.com/degu0055/postmansteps/refs/heads/main/images/getAssignmentList2.gif) 

Use the following API request:
1. Replace `https://rest-api.azurewebsites.net/api/` with your base URL.
2. Append `getAssignmentList?courseId=cst8911` to it.

Result:
```json
    {
        "id": "0aeec4c5-eee0-426e-8655-f7b09d1499da",
        "courseId": "cst8915",
        "assignmentId": "Assignment1",
        "title": "First Assignment",
        "content": "Cloud native assignment 1",
        "createdDate": "2025-02-17T04:23:19.545Z",
        "lastUpdated": "2025-02-17T04:23:19.545Z"
    }
```



