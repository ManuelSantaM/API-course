# First Task - CURL request
#### Todoist REST API by Manuel Santa Maria

**Pre-condition** 
1. Set the User and ApiToken
> export token=07278453ae927fc91d55a9c25185dc8fdc6ff83a
>
> echo $token



### **GET**

GET all projects **Project** by ID.

```shell
curl -X GET https://app.todoist.com/api/v9.223/projects/ -H "Authorization: Bearer $token"

```
Output to file
```shell
curl https://api.todoist.com/rest/v2/projects -H "Authorization: Bearer $token" -o output.json

```
See the details of the response
```shell
curl "https://api.todoist.com/rest/v2/projects" -H "Authorization: Bearer $token" -v

```

### **POST**

Create a new **Project**.
```shell
curl "https://api.todoist.com/rest/v2/projects" -X POST  --data '{ "name": "Manuel Project" }' -H "Content-Type: application/json" -H "Authorization: Bearer $token"
```

### **PUT**

Update the Name field of the **Project**.
```shell
curl "https://api.todoist.com/rest/v2/projects/6c75288422Hp9GXq" -X POST --data '{ "name": "Another One Bites the dust" }' -H "Content-Type:application/json" -H "Authorization: Bearer $token"
```
In this case the method is not allowed but, we tried.

### **DELETE**

Delete an **Issue** by ID.

```shell
curl -X DELETE "https://api.todoist.com/rest/v2/projects/2354953504" -H "Authorization: Bearer $token"
```

### **NEGATIVE CASES**
1. GET on non existent project.
```shell
curl "https://api.todoist.com/rest/v2/projects/9999999999" -H "Authorization: Bearer $token"
```
**Response:**

![alt text](image-1.png)


2. DELETE non existent project
```shell
curl -X DELETE "https://api.todoist.com/rest/v2/projects/9999999999" -H "Authorization: Bearer $token"
```

**Response:**
No reply at all, same as when deleting on an existin project. 
Might be a bug.

![alt text](image-2.png)

3. POST on non existent project
```shell
curl "https://api.todoist.com/rest/v2/projects/999999999"  -X POST   --data '{ "name": "Things To Buyonesa" }'  -H "Content-Type: application/json" -H "Authorization: Bearer $token"

```
**Response:**

![alt text](image-3.png)


4.  Attempt to PATCH on existing project, but Method is not allowed

```shell
curl "https://api.todoist.com/rest/v2/projects/6c75288422Hp9GXq"  -X PATCH   --data '{ "name": "Things To Buyonesa" }'  -H "Content-Type: application/json" -H "Authorization: Bearer $token"
```
**Response:**

![alt text](image-4.png)


