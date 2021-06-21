# REST API request & response formats
Common RESTful API response formats which we use across all our projects

**Based on [JSend](https://github.com/omniti-labs/jsend)**

## Response
<table>
<tr>
    <th>Key</th><th>Description</th>
</tr>
<tr>
    <td>status</td>
    <td>result status of the request. Mostly "success" or "fail"</td>
</tr>
<tr>
    <td>data</td>
    <td>Actual response for the request (in JSON format)</td>
</tr>
<tr>
    <td>message</td>
    <td>Brief message from the server about the status of the request.</td>
</tr>
<tr>
    <td>error</td>
    <td>Error code and message in JSON format. Mostly available only if error occurs</td>
</tr>
<tr>
    <td>log</td>
    <td>Multiple action messages for larger operations</td>
</tr>
</table>

## Requests ##
 - URL always should be small letters. Use hyphen to separate.
 - Should use provided API request methods as per standards. (GET, POST, PUT, DELETE)
 - Controller name can be singular or plural as per requirements.

## Examples

### GET ### 
Use GET requests to retrieve resource representation/information only

#### api/employees ####
```
{
    status : "success",
    data : {
         [
            { "id" : 1, "name" : "Anbu", "phone" : "9348753984" },
            { "id" : 2, "name" : "Jay", "phone" : "2987394488" },
        ]
     }
}
```
#### api/employees/2 ####
```
{
    status : "success",
    data : { "id" : 2, "name" : "Jay", "phone" : "2987394488" }
}
```
#### api/employees/3873 ####
```
{
    status : "fail",
    message: "Employee not found"
}
```

#### api/employees ####
```
{
    "status" : "error",
    "message" : "Unable to communicate with database"
}
```
###POST ###
Always use POST for CREATE operations.

#### api/employees ####
```
{
    "status" : "success",
    "message" : "Employee created successfully"
}
```
#### api/employees ####
```
{
    "status" : "fail",
    "message" : "Something went wrong",
    "error": {"code": 405, "message": "Unautorized access"}
}
```

### PUT ###
Use PUT APIs primarily to update existing resource 
(if the resource does not exist, then API may decide to create a new resource or not)

#### api/employees/1 ####
```
{
    "status" : "success",
    "message" : "Employee updated successfully",
}
```

### DELETE ###

#### api/employees/1 ####
```
{
    "status" : "success",
    "message" : "Employee deleted successfully",
}
```