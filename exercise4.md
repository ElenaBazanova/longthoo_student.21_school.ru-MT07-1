### 1. Проверка эндпойнта GET ​/api​/v1​/Activities

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 386058c8-8f10-458e-b443-cb8b53be195f  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  

**Тело запроса** отсутствует

**Заголовки ответа**   
Content-Type: application/json; charset=utf-8; v=1.0  
Date: Wed, 14 Jun 2023 17:18:08 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
api-supported-versions: 1.0  

**Тело ответа**
```
[  
    {  
        "id": 1,  
        "title": "Activity 1",  
        "dueDate": "2023-06-14T18:18:08.8938896+00:00",  
        "completed": false  
    },
    ...  
     {
        "id": 30,  
        "title": "Activity 30",  
        "dueDate": "2023-06-15T23:18:08.8938998+00:00",  
        "completed": true  
    }  
]
```

### 2. Проверка эндпоинта POST ​/api​/v1​/Activities (провальный)

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/43

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 201 Created, тело ответа в формате JSON

**Заголовки запроса**   
User-Agent: PostmanRuntime/7.32.2    
Accept: */*    
Postman-Token: c8a29c21-2176-43b1-8be0-581e4980517c   
Host: fakerestapi.azurewebsites.net   
Accept-Encoding: gzip, deflate, br   
Connection: keep-alive   
Content-Length: 0  

**Тело запроса**   
```
{  
  "id": 43,   
  "title": "string",   
  "dueDate": "2023-06-14T18:05:52.275Z",  
  "completed": true  
}  
```
**Заголовки ответа**   
Content-Type: application/problem+json; charset=utf-8   
Date: Wed, 14 Jun 2023 17:31:57 GMT   
Server: Kestrel   
Transfer-Encoding: chunked   

**Тело ответа**
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",  
    "title": "Unsupported Media Type",  
    "status": 415,  
    "traceId": "00-6830885fc7329c4ea537d26df0adc2b0-671ab77a30d45e42-00"  
}
```

### 3. Проверка эндпоинта POST ​/api​/v1​/Activities (провальный, id 121212121212121)

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{activityfail-id}}

**Ожидаемый результат**
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**   
Content-Type: application/json   
User-Agent: PostmanRuntime/7.32.2     
Accept: */*     
Postman-Token: 0b140f59-5c1f-48d4-a3ca-f39e8bf9c284     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 115     

**Тело запроса**
```
{  
  "id": 121212121212121,  
  "title": "string",    
  "dueDate": "2023-06-14T16:17:49.340Z",  
  "completed": true  
}  
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Wed, 14 Jun 2023 17:40:51 GMT      
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-d03da5ce0621404d930c859f78a4b3e1-a083ed2ec011ef43-00",  
    "errors": {  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 1 |   BytePositionInLine: 23."  
        ]  
    }  
} 
```

### 4. Проверка эндпоинта POST ​/api​/v1​/Activities (некорректный код запроса)

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Activities>  

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**          
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.2     
Accept: */*     
Postman-Token: b9e0bff6-ee58-4b25-a231-bb7a28c882d9     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 97     

**Тело запроса** 
```

    "id": 13,
 "title": "string",
 "dueDate": "2023-06-12T20:43:45.215Z",
 "completed": true
   
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Wed, 14 Jun 2023 17:56:15 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-92a476bb08c1344598f5858b28532eff-5a6810c14eaee541-00",  
    "errors": {  
        "$": [  
            "The JSON value could not be converted to   FakeRestAPI.Models.Activity. Path: $ | LineNumber: 0 |   BytePositionInLine: 4."  
        ]  
    }  
}  
```
 
### 5. Проверка эндпоинта POST ​/api​/v1​/Activities (изменение типа значений)

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Activities>  

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.2     
Accept: */*     
Postman-Token: 9fb61820-ef21-463a-806c-af01d37cffa0     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 104     

**Тело запроса**
```
{  
  "id": null,  
  "title": "string",  
  "dueDate": "2023-06-14T18:05:52.275Z",  
  "completed": true  
}  
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Wed, 14 Jun 2023 18:10:59 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
```  
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-07d41345c462c64985ea4f415bdf0dcb-b7fd2c68e3b8524e-00",  
    "errors": {  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 1 |   BytePositionInLine: 12."  
        ]  
    }  
}  
```

### 6. Проверка эндпоинта POST ​/api​/v1​/Activities (изменение типа значений)

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Activities>  

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, запрос не исполнен, тело ответа в формате JSON

**Заголовки запроса**      
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.2     
Accept: */*     
Postman-Token: 0b38e8a5-7fef-41a6-a003-dd36d29d6538     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 112     

**Тело запроса** 
```
{  
  "id": ,    
  "title": "string",    
  "dueDate": "2023-06-14T18:05:52.275Z",    
  "completed": true    
}    
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Wed, 14 Jun 2023 18:18:50 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       

**Тело ответа**
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-a52debf1779c444cb5342eb003556460-f4884c25ea9a984a-00",  
    "errors": {  
        "$.id": [  
            "',' is an invalid start of a value. Path: $.id |   LineNumber: 1 | BytePositionInLine: 8."  
        ]  
    }  
}  
```

### 7. Проверка эндпоинта GET ​/api​/v1​/Activities​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{activity-id}}  

**Ожидаемый результат**     
получена активность с идентификатором 1, тело ответа в формате JSON, код состояния ответа 200 ОК

**Заголовки запроса**                  
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: f5fce039-27df-4f91-ad9f-d7be047b08e5       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       

**Тело запроса**  отсутствует  

**Заголовки ответа**       
Content-Type: application/json; charset=utf-8; v=1.0       
Date: Wed, 14 Jun 2023 18:27:49 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       
api-supported-versions: 1.0       

**Тело ответа**   

```
{  
    "id": 1,  
    "title": "Activity 1",  
    "dueDate": "2023-06-14T19:27:50.1203881+00:00",  
    "completed": false  
}  
```

### 8. Проверка эндпоинта GET ​/api​/v1​/Activities​/{id} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{{activityfail-id}} 

**Ожидаемый результат**     
запрос не возможно исполнить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**                    
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 16a2984c-2563-4971-9356-614d00462b9a       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive        

**Тело запроса**  отсутствует  

**Заголовки ответа**         
Content-Type: application/problem+json; charset=utf-8       
Date: Wed, 14 Jun 2023 18:37:08 GMT       
Server: Kestrel       
Transfer-Encoding: chunked      

**Тело ответа**   
``` 
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-5f1a120f59a31e42bf4f5985bdb27ea9-eed2d7bf83b4f14d-00",  
    "errors": {  
        "id": [  
            "The value '{}' is not valid."  
        ]  
    }  
}  
```

### 9. Проверка эндпоинта GET ​/api​/v1​/Activities​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{}}

**Ожидаемый результат**     
запрос невозможно отправить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**                    
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 0696700f-75e4-4b3c-bcd5-5a14c3b6564a       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       

**Тело запроса**  отсутствует    

**Заголовки ответа**             
Content-Type: application/problem+json; charset=utf-8       
Date: Wed, 14 Jun 2023 18:51:00 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       

**Тело ответа**  
``` 
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,   
    "traceId": "00-ce8828e5093a8f43813bf88f842c2b09-  d8d6722edd5e7541-00",  
    "errors": {  
        "id": [  
            "The value '{{}}' is not valid."  
        ]   
    }  
}  
```

### 10. Проверка эндпоинта PUT ​/api​/v1​/Activities​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{activity-id}}  

**Ожидаемый результат**     
изменение активности с идентификаторои 12, код состояния 200 ОК, формат тела ответа JSON

**Заголовки запроса**                           
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: eda08112-053b-49ec-bbc4-e24ba2b3a4a6       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 102       

**Тело запроса**
```
{  
  "id": 12,  
  "title": "string",  
  "dueDate": "2023-06-14T18:58:07.043Z",  
  "completed": true  
}  
```

**Заголовки ответа**                    
Content-Type: application/json; charset=utf-8; v=1.0       
Date: Wed, 14 Jun 2023 19:01:57 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       
api-supported-versions: 1.0       

**Тело ответа**    
``` 
{  
    "id": 12,  
    "title": "string",  
    "dueDate": "2023-06-14T18:58:07.043Z",  
    "completed": true
} 
```

### 11. Проверка эндпоинта PUT ​/api​/v1​/Activities​/{id} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/1 

**Ожидаемый результат**     
изменение активности с идентификаторои 12, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**                        
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 923bc77b-2efb-4221-9c58-14a487313255       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 115       

**Тело запроса**
```
{  
  "id": 121212145454545,  
  "title": "string",  
  "dueDate": "2023-06-14T18:58:07.043Z",  
  "completed": true  
}
```

**Заголовки ответа**               
Content-Type: application/problem+json; charset=utf-8       
Date: Wed, 14 Jun 2023 19:19:59 GMT        
Server: Kestrel       
Transfer-Encoding: chunked       

**Тело ответа**    
``` 
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-5e85b19836e14c4a819bbc857941d814-9b4168bb26e6ac4c-00",  
    "errors": {  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 1 |   BytePositionInLine: 23."  
        ]  
    }  
}  
```

### 12. Проверка эндпоинта PUT ​/api​/v1​/Activities​/{id} некорректный код запроса

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{putincorrect-id}} 

**Ожидаемый результат**     
невозможно изменение активности с идентификаторои 121212145454545, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**                        
Content-Type: application/json      
User-Agent: PostmanRuntime/7.32.2      
Accept: */*      
Postman-Token: 08a77836-5535-44ae-9fcf-af8896e64b24      
Host: fakerestapi.azurewebsites.net      
Accept-Encoding: gzip, deflate, br      
Connection: keep-alive      
Content-Length: 115      

**Тело запроса**
```
{  
  "id": 121212145454545,  
  "title": "string",  
  "dueDate": "2023-06-14T18:58:07.043Z",  
  "completed": true  
}  
```

**Заголовки ответа**               
Content-Type: application/problem+json; charset=utf-8     
Date: Wed, 14 Jun 2023 19:36:04 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
```  
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-5152e3c938650c49b7e16775ca50087c-8de8e490174e1b45-00",  
    "errors": {  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 1 |   BytePositionInLine: 23."  
        ]  
    }  
}  
```

### 13. Проверка эндпоинта PUT ​/api​/v1​/Activities​/{id} изменение типа значения

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/0  

**Ожидаемый результат**      
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**                          
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 53740f16-fe10-4d35-a8ca-1294652f4839       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 104       

**Тело запроса**
```
{   
  "id": null,  
  "title": "string",  
  "dueDate": "2023-06-14T18:58:07.043Z",  
  "completed": true  
} 
```

**Заголовки ответа**                   
Content-Type: application/problem+json; charset=utf-8       
Date: Wed, 14 Jun 2023 19:53:47 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       

**Тело ответа**
```  
{   
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-  a6afc83b0b3a694cbf6170a3e2848312-981aec68e5db3340-00",  
    "errors": {  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 1 |   BytePositionInLine: 12."  
        ]  
    }  
} 
```

### 14. Проверка эндпоинта PUT ​/api​/v1​/Activities​/{id} изменение типа значения

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/0  

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**                            
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 2405c501-44f1-44d6-9018-a1ef789dbe94       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 99       

**Тело запроса**
```
{  
  "id":,  
  "title": "string",  
  "dueDate": "2023-06-14T18:58:07.043Z",  
  "completed": true  
}  
```

**Заголовки ответа**                     
Content-Type: application/problem+json; charset=utf-8       
Date: Wed, 14 Jun 2023 20:07:13 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       

**Тело ответа** 
```  
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-  fd9d4c2497bc1c46b8c2ac07c29264aa-4dddcb83dab24342-00",  
    "errors": {  
        "$.id": [  
            "',' is an invalid start of a value. Path: $.id|   LineNumber: 1 | BytePositionInLine: 7."  
        ]  
    }  
}  
```

### 15. Проверка эндпоинта DELETE ​/api​/v1​/Activities​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/45  

**Ожидаемый результат**     
удалена активность с идентификатором 45, код состояния 200 ок

**Заголовки запроса**                           
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 731e476b-e904-4334-bf7d-7ed6489d1cd0       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       

**Тело запроса** отсутствует

**Заголовки ответа**                   
Content-Length: 0       
Date: Wed, 14 Jun 2023 20:12:47 GMT       
Server: Kestrel       
api-supported-versions: 1.0       

**Тело ответа** отсутствует   
  
### 17. Проверка эндпоинта PUT ​/api​/v1​/Activities​/{id} (отрицательный id)

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/1{{badactivity-id}}} 

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 415 Unsupported Media Type

**Заголовки запроса**                                
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 2dab777a-c337-4adc-aa51-a2c037685d86       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 101       

**Тело запроса**
```
{  
  "id":-1,  
  "title": "string",  
  "dueDate": "2023-06-14T18:58:07.043Z",  
  "completed": true  
}
```

**Заголовки ответа**       
Content-Type: application/json; charset=utf-8; v=1.0       
Date: Wed, 14 Jun 2023 20:46:02 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       
api-supported-versions: 1.0       

**Тело ответа** 
```
{  
    "id": -1,  
    "title": "string",  
    "dueDate": "2023-06-14T18:58:07.043Z",  
    "completed": true  
}

```

### 18. Проверка эндпоинта GET​/api​/v1​/Authors

**URL** https://fakerestapi.azurewebsites.net/api/v1/Authors

**Ожидаемый результат**     
сервер вернет ответ со списком авторов, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**                                  
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: b8edc93c-b3c6-4c83-9f7d-8949792f73f3       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       

**Тело запроса** отсутствует

**Заголовки ответа**         
Content-Type: application/json; charset=utf-8; v=1.0       
Date: Thu, 15 Jun 2023 04:02:08 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       
api-supported-versions: 1.0       

**Тело ответа**
```
[  
    {  
        "id": 1,  
        "idBook": 1,  
        "firstName": "First Name 1",  
        "lastName": "Last Name 1"  
    },  
    {  
        "id": 2,  
        "idBook": 1,  
        "firstName": "First Name 2",  
        "lastName": "Last Name 2"    
    },
    ...    
    {  
        "id": 588,  
        "idBook": 200,  
        "firstName": "First Name 588",  
        "lastName": "Last Name 588"  
    }  
]  
```

### 19. Проверка эндпоинта POST ​/api​/v1​/Authors положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Authors  

**Ожидаемый результат**     
сервер вернет ответ,изменив данные в книге с идентификатором 5 код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**                                    
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 317cfa60-2493-4cfd-87de-34494269aedf       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 82       

**Тело запроса**  
```
{  
  "id": 5,  
  "idBook": 5,  
  "firstName": "string",  
  "lastName": "string"  
}
``` 

**Заголовки ответа**      
Content-Type: application/json; charset=utf-8; v=1.0       
Date: Thu, 15 Jun 2023 05:07:59 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       
api-supported-versions: 1.0       

**Тело ответа**   
```
{  
    "id": 5,  
    "idBook": 5,  
    "firstName": "string",  
    "lastName": "string"  
}  
```

### 20. Проверка эндпоинта POST ​/api​/v1​/Authors провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Authors

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**                                       
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 6bbc1f15-2041-4df3-93d8-0691fb65233c       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 91       

**Тело запроса**    
```
{  
  "id": 12545689235  
  "idBook": 0,  
  "firstName": "string",  
  "lastName": "string"  
}  
 ```

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8       
Date: Thu, 15 Jun 2023 11:51:41 GMT       
Server: Kestrel       
Transfer-Encoding: chunked       

**Тело ответа**      
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-9fba085c0ec99d4a8978f67389ac2c02-972452af0f38f74e-00",  
    "errors": {  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 1 |   BytePositionInLine: 19."  
        ]  
    }  
}  
```

### 21. Проверка эндпоинта POST ​/api​/v1​/Authors некорректный код запроса

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors> 

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**                                         
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: 9afa95ed-0c3a-40a0-9ed9-b399074364aa       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 78       

**Тело запроса**  
```
{
 "id": 0,
 "idBook": 0,
 "firstName": "string",
 "lastName": "string"  
 }  
```

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8       
Date: Thu, 15 Jun 2023 12:04:08 GMT       
Server: Kestrel       
Transfer-Encoding: chunked        

**Тело ответа**          
```
{ 
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-5aefe6aa1a2fe049bd0eeadd18c2de77-3be1c8e893856542-00",  
    "errors": {  
        "$": [  
            "The JSON value could not be converted to   FakeRestAPI.Models.Author. Path: $ | LineNumber: 0 |   BytePositionInLine: 5."  
        ]  
    }  
}  
```

### 22. Проверка эндпоинта POST ​/api​/v1​/Authors изменение типа значений

**URL** https://fakerestapi.azurewebsites.net/api/v1/Authors 

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**                                           
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: e7bf276f-213c-4851-b604-e1f6ff02d5a2       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 78        

**Тело запроса**    
```
{  
 "id": null,  
 "idBook": 0,  
 "firstName": "string",  
 "title": "string"  
}  
``` 

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8       
Date: Thu, 15 Jun 2023 12:14:48 GMT       
Server: Kestrel       
Transfer-Encoding: chunked         

**Тело ответа**            
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-  df13b6b11266c34686c9af63d37bda7c-8c4d99bb20f2724d-00",  
    "errors": {  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 1 |   BytePositionInLine: 11."  
        ]  
    }  
}  
```

### 23. Проверка эндпоинта POST ​/api​/v1​/Authors пустой запрос

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors> 

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**                                             
Content-Type: application/json       
User-Agent: PostmanRuntime/7.32.2       
Accept: */*       
Postman-Token: f3bdd6bd-1bf4-485b-8760-625adfe406a7       
Host: fakerestapi.azurewebsites.net       
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       
Content-Length: 76       

**Тело запроса**      
```
{  
 "id":,  
 "idBook": 0,  
 "firstName": "string",  
 "lastName": "string"  
}    
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8       
Date: Thu, 15 Jun 2023 12:21:36 GMT       
Server: Kestrel       
Transfer-Encoding: chunked        
  
**Тело ответа**                
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-389effb15b0098408dd60b1caa2d138e-46413e8788060845-00",  
    "errors": {  
        "$.id": [  
            "',' is an invalid start of a value. Path: $.id |   LineNumber: 1 | BytePositionInLine: 6."  
        ]  
    }  
}  
```

### 24. Проверка эндпоинта POST ​/api​/v1​/Authors пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Authors/authors/books/{{idbook}}  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 200 ОК, получены сведения об авторе книги с идентификатором 45, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: e406b7dd-63f0-413c-a7df-d7c044f3a50c  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  

**Тело запроса** отсутствует    

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0  
Date: Thu, 15 Jun 2023 12:32:21 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
api-supported-versions: 1.0   
  
**Тело ответа**
```
[  
    {  
        "id": 134,  
        "idBook": 45,  
        "firstName": "First Name 134",  
        "lastName": "Last Name 134"  
    },  
    {  
        "id": 135,  
        "idBook": 45,  
        "firstName": "First Name 135",  
        "lastName": "Last Name 135"  
    }  
]  
```

### 25. Проверка эндпоинта GET​/api​/v1​/Authors​/authors​/books​/{idBook} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Authors/authors/books/{{authorsfail-id}}  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: c1945d10-8727-4117-a77b-8dc7ba7610de  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  

**Тело запроса** отсутствует    

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 12:45:10 GMT  
Server: Kestrel  
Transfer-Encoding: chunked   
  
**Тело ответа**  
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-96c42bbab4df714fa1ea0176ead68ece-  ef6fa1774713924f-00",  
    "errors": {  
        "idBook": [  
            "The value '12545689235' is not valid."  
        ]  
    }  
} 
```

### 26. Проверка эндпоинта GET​/api​/v1​/Authors​/{id} положительный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors/{{authorsname-id}}>  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 200 OK, получены сведения об авторе с идентификатором 23, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: a35fa74c-2714-44df-af7a-32b6cc58a161  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive   

**Тело запроса** отсутствует    

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0  
Date: Thu, 15 Jun 2023 13:14:12 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
api-supported-versions: 1.0  
  
**Тело ответа**  
```
{  
    "id": 23,  
    "idBook": 7,  
    "firstName": "First Name 23",  
    "lastName": "Last Name 23"  
}  
```

### 27. Проверка эндпоинта GET​/api​/v1​/Authors​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Authors/{{}}  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: ae8c3ad5-3b2f-4944-9626-b095e1c1ab4c  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive   

**Тело запроса** отсутствует    

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 13:31:09 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
  
**Тело ответа**   
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-7f96a03ca3ca1646be8acddd920255d6-5834d79a078cde44-00",  
    "errors": {  
        "id": [  
            "The value '{{}}' is not valid."  
        ]  
    }  
}  
```

## 28. Проверка эндпоинта GET​/api​/v1​/Authors​/{id} провальный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors/{{}}>  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**      
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 00a68632-de8f-47a2-bea7-4d31a9df510a  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  

**Тело запроса** отсутствует    

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 20:13:27 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
  
**Тело ответа**       
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-92b374f37a5b4f4cbb99e22008dc5b89-8cf5a2f0ab1bec45-00",  
    "errors": {  
        "id": [  
            "The value '2575885425' is not valid."  
        ]  
    }  
}  
```

### 29. Проверка эндпоинта GET​/api​/v1​/Authors​/authors​/books​/{idBook} пустой запрос

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors/authors/books/{{}}>  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 5cef198b-91af-4330-9362-36b7e24cd1e0  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  

**Тело запроса** отсутствует      

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 20:17:49 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
  
**Тело ответа**
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId":   "00-729cef22c087ad4a9ec5d39ba9092d13-8c7250c3f2ab7844-00",  
    "errors": {  
        "idBook": [  
            "The value '{{}}' is not valid."  
        ]  
    }  
}  
```
### 30. Проверка эндпоинта PUT​/api​/v1​/Authors​/{id} положительный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors/{{authors-id}}>  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 200 OK, обновлены сведения об авторе с идентификатором 5, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json  
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 926a3da6-1aec-43fe-aab9-30ccec2c5edf  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  
Content-Length: 88  

**Тело запроса** 
```
{
 "id": 5,
 "idBook": 0,
 "firstName": "string",
 "lastName": "string"
}
```

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0  
Date: Thu, 15 Jun 2023 20:25:31 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
api-supported-versions: 1.0  
   
**Тело ответа**
```
{  
    "id": 5,  
    "idBook": 0,  
    "firstName": "string",  
    "lastName": "string"  
}  
```

### 31. Проверка эндпоинта PUT​/api​/v1​/Authors​/{id} провальный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors/{{authorsfail2-id}}>  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 BAD REQUEST, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json  
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: e8fcb695-007c-4261-8aa2-4e5803f66c6b  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  
Content-Length: 97  

**Тело запроса**     
```
{
 "id": 2575885425,
 "idBook": 0,
 "firstName": "string",
 "lastName": "string"
}  
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 20:33:24 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
   
**Тело ответа** 
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-5e9283a111568e448a855feda1fda3fb-  b546028bf72ce14f-00",  
    "errors": {  
        "id": [  
            "The value '2575885425' is not valid."  
        ],  
        "$.id": [  
            "The JSON value could not be converted to   System.Int32. Path: $.id | LineNumber: 2 |   BytePositionInLine: 17."  
        ]  
    }  
}  
```
### 32. Проверка эндпоинта PUT​/api​/v1​/Authors​/{id} некорректный код запроса

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Authors/{{authors-idbook}}>  

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json  
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 3307d51e-3f8f-4ccd-a6d7-83deff087ce4  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  
Content-Length: 87  

**Тело запроса**
```
{
 "id": 2575885425,
 "idBook": 0,
 "firstName": "string",
 "lastName": "string"  
}  
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 20:39:49 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
   
**Тело ответа**
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-  bdf545af1a6c8c439ffdfc53cb36d3e3-2a165abe79d36b47-00",  
    "errors": {  
        "$": [  
            "The JSON value could not be converted to   FakeRestAPI.Models.Author. Path: $ | LineNumber: 0 |   BytePositionInLine: 5."  
        ]  
    }  
}  
```

### 33. Проверка эндпоинта PUT​/api​/v1​/Authors​/{id} изменение типа значений

**URL**  <https://fakerestapi.azurewebsites.net/api/v1/Authors/0>

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 415 Unsupported Media Type, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: c5ef5952-672c-499a-ac7d-e8f713cce0a1  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  
Content-Length: 0  

**Тело запроса**
```
 { 
 "id": null,
 "idBook": 0,
 "firstName": "string",
 "lastName": "string"
}    
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 20:43:51 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
   
**Тело ответа**
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",  
    "title": "Unsupported Media Type",  
    "status": 415,  
    "traceId": "00-   ac0d2b9fa93ca045a7ac0af6b6464700-7c16df90fe45e447-00"  
}  
```

### 34. Проверка эндпоинта PUT​/api​/v1​/Authors​/{id} пустой запрос

**URL**  <https://fakerestapi.azurewebsites.net/api/v1/Authors/0>

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Error: Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json  
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 6a3ec54e-c6d0-4bae-baf6-562836bca2f2  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  
Content-Length: 100  

**Тело запроса**
```
 { 
 "id":,
 "idBook": 0, 
 "firstName": "string",
 "lastName": "string"
}    
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 20:50:03 GMT   
Server: Kestrel  
Transfer-Encoding: chunked  
   
**Тело ответа**
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-  e8a8c0d43d474143917c402ceaca6031-74667bd5039e0e45-00",  
    "errors": {  
        "$.id": [  
            "',' is an invalid start of a value. Path: $.id |   LineNumber: 2 | BytePositionInLine: 6."  
        ]  
    }  
}  
```

## 35. Проверка эндпоинта DELETE​/api​/v1​/Authors​/{id} положительный

**URL**  <https://fakerestapi.azurewebsites.net/api/v1/Authors/{{authorsdelete-id}}>

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 200 OK, удалены сведения об авторе с идентификатором 1, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 316b48fb-e603-4627-98cb-6e6dcce00dc2  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  

**Тело запроса** отсутствует

**Заголовки ответа**     
Content-Length: 0  
Date: Thu, 15 Jun 2023 20:59:54 GMT  
Server: Kestrel  
api-supported-versions: 1.0  
   
**Тело ответа** отсутствует


### 36. Проверка эндпоинта DELETE​/api​/v1​/Authors​/{id} пустой запрос

**URL**  https://fakerestapi.azurewebsites.net/api/v1/Authors/{{}}

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: 50ad4d79-77af-4efa-8f1a-8bd1d8e22d21  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  

**Тело запроса** отсутствует

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8  
Date: Thu, 15 Jun 2023 21:05:42 GMT  
Server: Kestrel  
Transfer-Encoding: chunked  
   
**Тело ответа**
```
{  
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",  
    "title": "One or more validation errors occurred.",  
    "status": 400,  
    "traceId": "00-  e78694e257fa8646963b2ce0cd8defba-838a556f38786d46-00",  
    "errors": {  
        "id": [  
            "The value '{{}}' is not valid."  
        ]  
    }  
}  
```

### 37. Проверка эндпойнта PUT​/api​/v1​/Authors​/{id} провальный (отрицательное значение id)

**URL**  https://fakerestapi.azurewebsites.net/api/v1/Authors/{{badactivity-id}}

**Ожидаемый результат**     
сервер вернет ответ c кодом состояния 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json  
User-Agent: PostmanRuntime/7.32.2  
Accept: */*  
Postman-Token: d5538e5c-d053-4638-be8b-77d959c9d488  
Host: fakerestapi.azurewebsites.net  
Accept-Encoding: gzip, deflate, br  
Connection: keep-alive  
Content-Length: 66  

**Тело запроса**
```
{
  "id": -1,
  "userName": "string",
  "password": "string"
}
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 21:12:02 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-45622b38897bf748ae56617ca89e595a-c548c9bf30a5964b-00",
    "errors": {
        "id": [
            "The value ' ' is invalid."
        ]
    }
}
```

### 38. Проверка эндпоинта GET​/api​/v1​/Books

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Books>

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON 

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: e96e27c4-81c1-43ac-bde7-e60af04606de     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует 

**Заголовки ответа**      
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 15:29:34 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0 

**Тело ответа** 
``` 
[
    {
        "id": 1,
        "title": "Book 1",
        "description": "Lorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\n",
        "pageCount": 100,
        "excerpt": "Lorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\n",
        "publishDate": "2023-06-14T15:29:34.7308442+00:00"
    },
    ...
    {
        "id": 200,
        "title": "Book 200",
        "description": "Lorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\n",
        "pageCount": 20000,
        "excerpt": "Lorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\n",
        "publishDate": "2022-11-27T15:29:34.7331345+00:00"
    }
]
```

### 39. Проверка эндпоинта POST​/api​/v1​/Books положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON 

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 31c00837-5a7a-44ff-8647-14fd9003bf9d     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```
{
  "id": 23,
  "title": "string",
  "description": "string",
  "pageCount": 0,
  "excerpt": "string",
  "publishDate": "2023-06-15T15:58:35.000Z"
}
```

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 16:17:40 GMT     
Server: Kestrel
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа** 
```
{
    "id": 23,
    "title": "string",
    "description": "string",
    "pageCount": 0,
    "excerpt": "string",
    "publishDate": "2023-06-15T15:58:35Z"
}
```

### 40. Проверка эндпоинта POST​/api​/v1​/Books провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/235544888555

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 405 Method Not Allowed

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: b1421921-7e21-4362-bbc1-f29afaeed813     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
``` 
{
  "id": 2355448885554,
  "title": "string",
  "description": "string",
  "pageCount": 0,
  "excerpt": "string",
  "publishDate": "2023-06-15T15:58:35.000Z"
}
```

**Заголовки ответа**      
Content-Length: 0     
Date: Thu, 15 Jun 2023 17:13:52 GMT     
Server: Kestrel     
Allow: DELETE, GET, PUT     

**Тело ответа** отсутствует     

### Проверка эндпоинта POST​/api​/v1​/Books некорректный код запроса

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/null

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 405 Method Not Allowed

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 67023cd4-c9ac-4940-a463-0ebc83e1a0ce     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует 

**Заголовки ответа**      
Content-Length: 0     
Date: Thu, 15 Jun 2023 17:27:53 GMT     
Server: Kestrel     
Allow: DELETE, GET, PUT     

**Тело ответа** отсутствует


### 41. Проверка эндпоинта POST​/api​/v1​/Books изменение типа значений

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/{{authors-idbook}}

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 405 Method Not Allowed

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 67023cd4-c9ac-4940-a463-0ebc83e1a0ce     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует 

**Заголовки ответа**  
Content-Length: 0     
Date: Thu, 15 Jun 2023 17:27:53 GMT     
Server: Kestrel     
Allow: DELETE, GET, PUT     

**Тело ответа** отсутствует

### Проверка эндпоинта POST​/api​/v1​/Books пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/0

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 5621d6dd-ca65-4b50-b9ee-09c5f08fe77f     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** 
``` 
{
  "id":,
  "title": "string",
  "description": "string",
  "pageCount": 0,
  "excerpt": "string",
  "publishDate": "2023-06-15T17:36:09.392Z"
}
```

**Заголовки ответа**       
Content-Length: 0     
Date: Thu, 15 Jun 2023 17:44:34 GMT     
Server: Kestrel     
Allow: DELETE, GET, PUT     

**Тело ответа**
``` 
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-5236e0fe24e3f2449d9c02481712876c-34d38f48cb7b6541-00",
    "errors": {
        "$.id": [
            "',' is an invalid start of a value. Path: $.id | LineNumber: 1 | BytePositionInLine: 7."
        ]
    }
}
```

### 42. Проверка эндпоинта GET ​/api​/v1​/Books​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/1

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 2b49f055-e3f5-4677-bede-7f697464ac74     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 17:49:38 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа** 
```
{
    "id": 1,
    "title": "Book 1",
    "description": "Lorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\n",
    "pageCount": 100,
    "excerpt": "Lorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\nLorem lorem lorem. Lorem lorem lorem. Lorem lorem lorem.\n",
    "publishDate": "2023-06-14T17:49:39.7577736+00:00"
}
```

### 43. Проверка эндпоинта GET ​/api​/v1​/Books​/{id} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/121212121212121

**Ожидаемый результат**     
запрос не возможно исполнить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 6b95327c-5c77-4959-abbf-dab2ce237770     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 17:54:10 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
``` 
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-e4d399a08cbdd241a1c2cffbdddb66a0-f529194c8d0be04c-00",
    "errors": {
        "id": [
            "The value '121212121212121' is not valid."
        ]
    }
}
```

## 44. Проверка эндпоинта GET ​/api​/v1​/Books​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/{{}}

**Ожидаемый результат**     
запрос невозможно отправить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*          
Cache-Control: no-cache     
Postman-Token: 7580d49e-34d1-40b7-9022-7796198d69c9     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br          
Connection: keep-alive     

**Тело запроса** 
```
{
 "id":,
 "title": "string",
 "description": "string",
 "pageCount": 0,
 "excerpt": "string",
 "publishDate": "2023-06-12T12:57:35.034Z"
}
```

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:02:40 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-bc835fadacdee04fa1e08fcd2cfa48a9-e6b4bc07e085af41-00",
    "errors": {
        "id": [
            "The value '{{}}' is not valid."
        ]
    }
}
```

### 45. Проверка эндпоинта PUT​/api​/v1​/Books​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/{{activity-id}} 

**Ожидаемый результат**     
изменение активности с идентификаторои 12, код состояния 200 ОК, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: ffcbc55f-ca5b-4d6a-8ecf-8b78c3645010     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** 
```
{
  "id": 12,
  "title": "string",
  "description": "string",
  "pageCount": 0,
  "excerpt": "string",
  "publishDate": "2023-06-15T18:10:23.083Z"
} 
```

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 18:13:25 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа** 
```
{
    "id": 12,
    "title": "string",
    "description": "string",
    "pageCount": 0,
    "excerpt": "string",
    "publishDate": "2023-06-15T18:10:23.083Z"
}
```

### 46. Проверка эндпоинта PUT​/api​/v1​/Books​/{id} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/121212121212121

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 415 Unsupported Media Type

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 991e2997-9e95-47f3-878b-9bfadcc88262     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует
     
**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:16:47 GMT     
Server: Kestrel          
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",
    "title": "Unsupported Media Type",
    "status": 415,
    "traceId": "00-ea0ca9115262504cac00a593995041b0-41941770a2ac0043-00"
}
``` 
 
### 47. Проверка эндпоинта PUT​/api​/v1​/Books​/{id} некорректный код запроса

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/0

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 221f6836-8c16-4ddb-beff-75277160936d     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```
{
  "id":,
  "title": "string",
  "description": "string",
  "pageCount": 0,
  "excerpt": "string",
  "publishDate": "2023-06-15T18:10:23.083Z"
} 
``` 

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:24:15 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
``` 
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-b2a7312167049d4d90029909f381a1f6-28bdbe6def33c641-00",
    "errors": {
        "$.id": [
            "',' is an invalid start of a value. Path: $.id | LineNumber: 1 | BytePositionInLine: 7."
        ]
    }
}
```

### 48. Проверка эндпоинта PUT​/api​/v1​/Books​/{id} изменение типа значений

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/null

**Ожидаемый результат**     
Невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: b742f1ed-aa29-4f53-9d44-0837e3ebcff7     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** 
```
{
  "id":null,
  "title": "string",
  "description": "string",
  "pageCount": 0,
  "excerpt": "string",
  "publishDate": "2023-06-15T18:10:23.083Z"
}
```

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:27:31 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
``` 
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-9d061d475b95ed43a22ac2a425c21491-273b1ebdd4ff044a-00",
    "errors": {
        "id": [
            "The value 'null' is not valid."
        ],
        "$.id": [
            "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 1 | BytePositionInLine: 11."
        ]
    }
}
```

### 49. Проверка эндпоинта PUT​/api​/v1​/Books​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/0

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 221f6836-8c16-4ddb-beff-75277160936d     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```
{
  "id":,
  "title": "string",
  "description": "string",
  "pageCount": 0,
  "excerpt": "string",
  "publishDate": "2023-06-15T18:10:23.083Z"
}
```  

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:24:15 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-b2a7312167049d4d90029909f381a1f6-28bdbe6def33c641-00",
    "errors": {
        "$.id": [
            "',' is an invalid start of a value. Path: $.id | LineNumber: 1 | BytePositionInLine: 7."
        ]
    }
}
```

### 50. Проверка эндпоинта PUT​/api​/v1​/Books​/{id} провальный (отрицательное значение id)

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/{{badactivity-id}}

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 415 Unsupported Media Type

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: d47a7e5c-8289-49dc-a4e0-e51348b013e3     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:33:00 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",
    "title": "Unsupported Media Type",
    "status": 415,
    "traceId": "00-9f68f9a5f702a9429a6a4c396a1c45eb-71649f4fdbdd8a4f-00"
}
```

### 51. Проверка эндпоинта DELETE​/api​/v1​/Books​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/5

**Ожидаемый результат**     
удалена активность с идентификатором 5, код состояния 200 ок

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: a4f856f6-ccca-4f99-a3d7-f22eca56d1ee     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  отсутствует

**Заголовки ответа**       
Content-Length: 0     
Date: Thu, 15 Jun 2023 18:37:19 GMT     
Server: Kestrel     
api-supported-versions: 1.0     

**Тело ответа** отсутствует


### 52. Проверка эндпоинта DELETE​/api​/v1​/Books​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Books/null

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 6585775e-602c-45d6-9c55-e3a4a6e5e067     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:43:01 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-b8b6d88f0ed9674aa8508991d652c698-424a5746d5d8e64b-00",
    "errors": {
        "id": [
            "The value 'null' is not valid."
        ]
    }
}
```

### 53. Проверка эндпойнта GET/api/v1/CoverPhotos

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3   
Accept: */*          
Postman-Token: 386058c8-8f10-458e-b443-cb8b53be195f       
Host: calculated when request is sent      
Accept-Encoding: gzip, deflate, br       
Connection: keep-alive       

**Тело запроса** отсутствует

**Заголовки ответа**        
Content-Type: application/json; charset=utf-8; v=1.0       
Date: Thu, 15 Jun 2023 14:08:29 GMT       
Server: Kestrel       
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**    
```
[
    {
        "id": 1,
        "idBook": 1,
        "url": "https://placeholdit.imgix.net/~text?txtsize=33&txt=Book 1&w=250&h=350"
    },
 {
        "id": 200,
        "idBook": 200,
        "url": "https://placeholdit.imgix.net/~text?txtsize=33&txt=Book 200&w=250&h=350"
    }
]
```

### 54. Проверка эндпоинта POST ​/api​/v1​/CoverPhotos

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 201 Created, тело ответа в формате JSON

**Заголовки запроса**   
Content-Type: application/json   
User-Agent: PostmanRuntime/7.32.3    
Accept: */*    
Cache-Control: no-cache    
Postman-Token: 426a4fad-8d42-4f7a-8520-8338bdea302f    
Host: fakerestapi.azurewebsites.net    
Accept-Encoding: gzip, deflate, br    
Connection: keep-alive         

**Тело запроса** 
```
{
  "id": 1,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**        
Content-Type: application/json; charset=utf-8; v=1.0         
Date: Thu, 15 Jun 2023 16:19:56 GMT         
Server: Kestrel          
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**     
```
{
    "id": 1,
    "idBook": 0,
    "url": "string"
}
```

### 55. Проверка эндпоинта POST​/api​/v1​/CoverPhotos (провальный, id 7654325678908)

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/7654325678908 

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**       
Content-Type: application/json         
User-Agent: PostmanRuntime/7.32.3        
Accept: */*         
Cache-Control: no-cache          
Postman-Token: 19892ebc-82fa-40da-b414-38ec1cbca5e1         
Host: fakerestapi.azurewebsites.net          
Accept-Encoding: gzip, deflate, br         
Connection: keep-alive     

**Тело запроса**
```
{
 "id": 7654325678908,
 "idBook": 0,
 "url": "string"
}
```

**Заголовки ответа**         
Content-Length: 0     
Date: Thu, 15 Jun 2023 16:48:28 GMT     
Server: Kestrel     
Allow: DELETE, GET, PUT       

**Тело ответа** 
``` 
{
  "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
  "title": "One or more validation errors occurred.",
  "status": 400,
  "traceId": "00-f1d39145b92ecb48bb1fdcea4e696f82-d3ef447eed6a2646-00",
  "errors": {
    "$.id": [
      "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 0 | BytePositionInLine: 19."
    ]
  }
}
```

### 56. Проверка эндпоинта POST​/api​/v1​/CoverPhotos (изменение типа значений)

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos>  

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**            
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: a23fee0b-2a5c-4cae-b2df-1305c07c7aee     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive      

**Тело запроса** 
```
{
  "id": null,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:52:20 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**    
```
 {
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-987b4f46e7a56b448dd7573407c0e9eb-7b795b43a60cbf44-00",
    "errors": {
        "$.id": [
            "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 1 | BytePositionInLine: 12."
        ]
    }
}
```

### 57. Проверка эндпоинта POST​/api​/v1​/CoverPhotos (пустой)

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos>  

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**         
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 6d16300c-e96d-475a-b245-fa8d1db8d054     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**   
```
{
  "id": ,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 18:56:34 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**    
```
 {
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-989e057a4b65c64abba08369a3b5f2e4-fc1ba6b32132d146-00",
    "errors": {
        "$.id": [
            "',' is an invalid start of a value. Path: $.id | LineNumber: 1 | BytePositionInLine: 7."
        ]
    }
}
```

### 58. Проверка эндпоинта GET ​/api​/v1​/CoverPhotos​/books​/covers​/{id 12} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/books/covers/12 

**Ожидаемый результат**
получена активность с идентификатором 12, тело ответа в формате JSON, код состояния ответа 200 ОК

**Заголовки запроса**           
User-Agent: PostmanRuntime/7.32.3           
Accept: */*              
Cache-Control: no-cache                   
Postman-Token: 788e1d0f-0494-4892-9a31-4f68105eb14e                   
Host: fakerestapi.azurewebsites.net                
Accept-Encoding: gzip, deflate, br                 
Connection: keep-alive     

**Тело запроса**  отсутствует  

**Заголовки ответа**       
Content-Type: application/json; charset=utf-8; v=1.0              
Date: Thu, 15 Jun 2023 19:00:21 GMT              
Server: Kestrel               
Transfer-Encoding: chunked      
api-supported-versions: 1.0     

**Тело ответа**   
```
[
    {
        "id": 12,
        "idBook": 12,
        "url": "https://placeholdit.imgix.net/~text?txtsize=33&txt=Book 12&w=250&h=350"
    }
] 
```

### 59. Проверка эндпоинта GET ​/api​/v1​/CoverPhotos​/books​/covers​/{id 125432566543245543}  провальный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/books/covers/125432566543245543>  

**Ожидаемый результат**     
запрос не возможно исполнить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**       
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: d6f2a345-e644-4d53-b2c6-f9d8fc1da642     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  отсутствует  

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 19:13:54 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**   
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-9bded8370fb45a4cbd1834e4fc54678b-349e46abe13fd24f-00",
    "errors": {
        "idBook": [
            "The value '125432566543245543' is not valid."
        ]
    }
}
```

### 60. Проверка эндпоинта GET ​/api​/v1​/CoverPhotos​/books​/covers​/{id} пустой

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{}}

**Ожидаемый результат**     
запрос невозможно отправить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**                  
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 199b6810-37e1-429c-8a35-1f70c1b39157     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  отсутствует

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 19:20:59 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**   
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-4864153a0915ad4e926873b7ea5fc45a-e7f3a138c8a28745-00",
    "errors": {
        "id": [
            "The value '{{}}' is not valid."
        ]
    }
}

```

### 61. Проверка эндпоинта GET​/api​/v1​/CoverPhotos​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/5

**Ожидаемый результат**       
Сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**                        
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 53c5c7e6-89b5-4b6b-8328-12068149c96d     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  отсутствует

**Заголовки ответа**       
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 19:28:04 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**  
```
{
    "id": 5,
    "idBook": 5,
    "url": "https://placeholdit.imgix.net/~text?txtsize=33&txt=Book 5&w=250&h=350"
}
```

### 62. Проверка эндпоинта GET​/api​/v1​/CoverPhotos​/{id 598765432456789} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/5

**Ожидаемый результат**       
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**      
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: b5de007f-6d41-45be-ba41-173952585b83     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 19:33:04 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**  
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-0c589606ae2f0243bb13075aac680353-622d1b09c9364345-00",
    "errors": {
        "id": [
            "The value '598765432456789' is not valid."
        ]
    }
}
```

### 63. Проверка эндпоинта GET ​/api​/v1​/CoverPhotos​​/{id} пустой

**URL** https://fakerestapi.azurewebsites.net/api/v1/Activities/{{}}

**Ожидаемый результат**     
запрос невозможно отправить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**      
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 1747dffc-6ae2-4791-8c65-978e128fd197     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Response Headers     

**Тело запроса** отсутствует

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 19:37:33 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**   
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-e332d199ce82194f981a7675229fa5ec-350a75c3ddfdac4b-00",
    "errors": {
        "id": [
            "The value '{{}}' is not valid."
        ]
    }
}
```

### 64. Проверка эндпоинта PUT​/api​/v1​/CoverPhotos​/{id 1} положительный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/1>

**Ожидаемый результат**     
изменение активности с идентификаторои 12, код состояния 200 ОК, формат тела ответа JSON

**Заголовки запроса**                      
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 657a68d1-1d5a-4890-9b19-5482a1d9728d     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
  "id": 1,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 20:03:04 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**
```  
{
 "id": 1,
 "idBook": 0,
 "url": "string"
}
```

### 65. Проверка эндпоинта PUT​/api​/v1​/CoverPhotos​/{id 14325464321345678} провальный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/14325464321345678>

**Ожидаемый результат**     
изменение активности с идентификаторои 12, код состояния 200 ОК, формат тела ответа JSON

**Заголовки запроса**                      
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 0325c239-d0a1-4043-83d1-5b97bc6eef44     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
  "id": 14325464321345678,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 20:06:29 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**    
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-993432a572e6bd44a3de6dccf1401cb2-2995b9d11caf944c-00",
    "errors": {
        "id": [
            "The value '14325464321345678' is not valid."
        ],
        "$.id": [
            "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 1 | BytePositionInLine: 25."
        ]
    }
}
```

### 66. Проверка эндпоинта PUT​/api​/v1​/CoverPhotos​/{} пустой 

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/{{}}

**Ожидаемый результат**     
запрос невозможно отправить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**      
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: f1cc762e-cf19-47fb-b826-858eed639792     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
  "id": ,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**        
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 20:13:14 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**  
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-763520d3afc9ac49b7d7bd5581397249-12793cc72045574f-00",
    "errors": {
        "id": [
            "The value '{{}}' is not valid."
        ],
        "$.id": [
            "',' is an invalid start of a value. Path: $.id | LineNumber: 1 | BytePositionInLine: 8."
        ]
    }
}
```

### 67. Проверка эндпоинта DELETE​/api​/v1​/CoverPhotos​/{id} положительный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/16>

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**                                    
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 79f4dbac-d736-44cd-ac7c-33f1a13eef91     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**       
Content-Length: 0     
Date: Thu, 15 Jun 2023 20:16:24 GMT     
Server: Kestrel     
api-supported-versions: 1.0     

**Тело ответа** отсутствует


### 68. Проверка эндпоинта DELETE​/api​/v1​/CoverPhotos​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/{{}}

**Ожидаемый результат**     
запрос невозможно отправить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**        
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: bec076ee-6cf6-4141-8b99-75cec47db909     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 20:23:27 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**  
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-3fc250daf35ff3409f2b8fb419a91cf8-ac8ee61dddfd2a4e-00",
    "errors": {
        "id": [
            "The value '{{}}' is not valid."
        ]
    }
}
```

### 69. Проверка эндпоинта POST ​/api​/v1​/CoverPhotos некорректный код запроса

**URL** https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/

**Ожидаемый результат**     
запрос невозможно отправить, тело ответа в формате JSON, код состояния ответа 400 Bad Request

**Заголовки запроса**        
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 7cdc963b-5cfc-4765-ad16-1f473980b9ef     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
 "id": 0,
 "idBook": 0,
 "url": "string"
}
```

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 20:28:39 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**  
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-48ddec0a60eb0d49b98c5e30960bb0fb-99023cd5026b0545-00",
    "errors": {
        "$.id": [
            "',' is an invalid start of a value. Path: $.id | LineNumber: 1 | BytePositionInLine: 8."
        ]
    }
}
```

### 70. Проверка эндпоинта PUT​/api​/v1​/CoverPhotos​/{id 0} положительный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/1>

**Ожидаемый результат**     
изменение активности с идентификаторои, код состояния 200 ОК, формат тела ответа JSON

**Заголовки запроса**       
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: d82a1f14-bf15-4fad-bb17-29b62f650c3f     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
  "id": 0,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 20:34:56 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**    
 ``` 
{
 "id": 0,
 "idBook": 0,
 "url": "string"
}
```

### 71. Проверка эндпоинта PUT​/api​/v1​/CoverPhotos​/{id} изменение типа значений

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos>  

**Ожидаемый результат**     
сервер вернет ответ с кодом состояния - 400 Bad Request, тело ответа в формате JSON

**Заголовки запроса**              
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: f767a24a-0d16-4954-a087-5651aba4360a     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
  "id": null,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Thu, 15 Jun 2023 20:43:45 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**    
```
 {
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-e9aab75a48604b4bbb18dfcab88655d0-ef5634d2cdb72a42-00",
    "errors": {
        "id": [
            "The value 'null' is not valid."
        ],
        "$.id": [
            "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 2 | BytePositionInLine: 10."
        ]
    }
}
```

### 72. Проверка эндпоинта PUT​/api​/v1​/CoverPhotos​/{id} провальный (отрицательное значение id)

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/1>

**Ожидаемый результат**     
изменение активности с идентификаторои, код состояния 200 ОК, формат тела ответа JSON

**Заголовки запроса**           
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 0c8320df-3e46-45ab-8aff-da93db2ff1c1     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
  "id": -1,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Thu, 15 Jun 2023 20:46:03 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**    
```
{
  "id": -1,
  "idBook": 0,
  "url": "string"
}
```


### 73. Проверка эндпоинта PUT​/api​/v1​/CoverPhotos/{id} некорректный код запроса

**URL** <https://fakerestapi.azurewebsites.net/api/v1/CoverPhotos/0>

**Ожидаемый результат**     
изменение активности с идентификаторои, код состояния 200 ОК, формат тела ответа JSON

**Заголовки запроса**           
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*          
Cache-Control: no-cache     
Postman-Token: eb81c08c-1ba0-4650-a3f0-1a312c2f70e2     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**  
```
{
  "id": 0,
  "idBook": 0,
  "url": "string"
}
```

**Заголовки ответа**        
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Fri, 16 Jun 2023 09:18:48 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**    
```
{
  "id": 0,
  "idBook": 0,
  "url": "string"
}
```

### 74. Проверка эндпойнта GET​/api​/v1​/Users

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Users>

**Ожидаемый результат**     
сервер вернет ответ со списком пользователей, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Postman-Token: 3e3f13ec-64dd-4c63-84a6-fa729d342d0d     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Fri, 16 Jun 2023 06:03:48 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**
```
[
    {
        "id": 1,
        "userName": "User 1",
        "password": "Password1"
    },
    ......
     {
        "id": 10,
        "userName": "User 10",
        "password": "Password10"
    }
]
```

### 75. Проверка эндпойнта POST​/api​/v1​/Users положительный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Users>

**Ожидаемый результат**     
сервер вернет ответ с информацией о добавлении пользователя с идентификатором 19, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Postman-Token: a404da55-caf7-4f72-a639-5256bd80abc0     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 63     

**Тело запроса** 
```
{
 "id": 19,
 "userName": "string",
 "password": "string"
}
```

**Заголовки ответа**     
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Fri, 16 Jun 2023 06:11:01 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа**
```
{
    "id": 19,
    "userName": "string",
    "password": "string"
}
```

### 76. Проверка эндпоинта POST​/api​/v1​/Users провальный

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Users>

**Ожидаемый результат**     
сервер вернет ответ с ошибкой код состояния ответа 400- Bad Request, тело ответа в формате JSON

**Заголовки запроса**

Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Postman-Token: be2bfccc-ce83-4ee7-8b5e-9bf057e8ed6a     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 78     

**Тело запроса**

```
{
 "id":{{usersfail-id}},
 "userName": "string",
 "password": "string"
}
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 06:28:54 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
```
[
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-8c4ffe2f237db0498e6698a0bb91fb6d-b9ed8d60ba54be4c-00",
    "errors": {
        "$.id": [
            "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 1 | BytePositionInLine: 24."
        ]
    }
]
```

### 77. Проверка эндпоинта POST​/api​/v1​/Users некорректный код запроса

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Users>

**Ожидаемый результат**     
сервер вернет ответ с ошибкой код состояния ответа 400- Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Postman-Token: a054458c-8a9d-42d5-b9f8-7f0c18796c1b     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 60     

**Тело запроса**
```
[
  "id": 0,
  "userName": "string",
  "password": "string
]
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 07:45:22 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-99fb42419ec3d043b0db97609dbd97e6-141854164e07e643-00",
    "errors": {
        "$": [
            "The JSON value could not be converted to FakeRestAPI.Models.User. Path: $ | LineNumber: 1 | BytePositionInLine: 6."
        ]
    }
}
```

### 78. Проверка эндпоинта POST ​/api​/v1​/Activities (изменение типа значений)

**URL** <https://fakerestapi.azurewebsites.net/api/v1/Users>

**Ожидаемый результат**     
сервер вернет ответ с ошибкой код ответа 400 Error: Bad Request, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Postman-Token: 896a87a9-134b-4c25-99ee-ee45e4a0b075     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     
Content-Length: 65     

**Тело запроса** 
```
{
 "id": null,
 "userName": "string",
 "password": "string"
}
```

**Заголовки ответа**     
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 07:52:00 GMT     
Server: Kestrel     
Transfer-Encoding: chunked          

**Тело ответа**
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-d8984f997097c94ba6d3dd86dcde999a-c7e82018cf998b4b-00",
    "errors": {
        "$.id": [
            "The JSON value could not be converted to System.Int32. Path: $.id | LineNumber: 1 | BytePositionInLine: 11."
        ]
    }
}
```

### 79. Проверка эндпоинта POST​/api​/v1​/Users пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 669a9776-e21c-4d3f-b2e3-df5d1c50ef24     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```  
{
  "id":,
  "userName": "string",
  "password": "string"
}
```

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 08:40:49 GMT     
Server: Kestrel     
Transfer-Encoding: chunked      

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-0ddfd3f5d155bb438f689c467318c470-eac7441fc89e084d-00",
    "errors": {
        "$.id": [
            "',' is an invalid start of a value. Path: $.id | LineNumber: 1 | BytePositionInLine: 7."
        ]
    }
}
```

### 80. Проверка эндпоинта GET ​/api​/v1​/Users/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/6

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON 

**Заголовки запроса**      
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 23375d80-a22c-4ba9-a593-1fed73a7ec58     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**      
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Fri, 16 Jun 2023 09:07:45 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0      

**Тело ответа**
```
{
    "id": 6,
    "userName": "User 6",
    "password": "Password6"
}
```

### 81. Проверка эндпоинта GET ​/api​/v1​/Users/{id} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/191213141516171819

**Ожидаемый результат**      
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 0cd1d2fd-c62c-464f-82cd-b26e0e5a9326     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 09:11:00 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
``` 
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-31e63543532fa24f824b33d5000c3c59-3fb4e26a721db14d-00",
    "errors": {
        "id": [
            "The value '191213141516171819' is not valid."
        ]
    }
}
```


### 82. Проверка эндпоинта GET ​/api​/v1​/Users​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/{{}} 

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 01e6b85c-0eb8-4027-9f5d-735589942df6     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```  
{
  "id":,
  "userName": "string",
  "password": "string"
}
```

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 09:25:02 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-e8fd68ee99e0a64a92817f310609bad4-e4eb19295171d147-00",
    "errors": {
        "id": [
            "The value '{{}}' is not valid."
        ]
    }
}
```

### 83. Проверка эндпоинта PUT​/api​/v1​/Users​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/2

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 76f40509-cda3-439a-93ef-87b912ee6699     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```  
{
 "id":2 ,
 "userName": "string",
 "password": "string"
}
```

**Заголовки ответа**       
Content-Type: application/json; charset=utf-8; v=1.0     
Date: Fri, 16 Jun 2023 09:38:48 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     
api-supported-versions: 1.0     

**Тело ответа** 
```
{
    "id": 2,
    "userName": "string",
    "password": "string"
}
```

### 84. Проверка эндпоинта PUT​/api​/v1​/Users​/{id} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/191213141516171819

**Ожидаемый результат**
невозможно исполнить запрос, код состояния 415 Unsupported Media Type

**Заголовки запроса**
User-Agent: PostmanRuntime/7.32.3
Accept: */*
Cache-Control: no-cache     
Postman-Token: d2d88d67-cf44-4930-aa38-79746733a0e7     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive      

**Тело запроса** отсутствует

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 09:41:43 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",
    "title": "Unsupported Media Type",
    "status": 415,
    "traceId": "00-d31eb4c68d99ce46a997a382fbaae239-78a59d730d2c3045-00"
}
```

### 85. Проверка эндпоинта PUT​/api​/v1​/Users​/{id} некорректный код запроса

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/{{Users​-0}}

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 405 Method Not Allowed, формат тела ответа JSON

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 0d147bac-1c40-4bce-837c-359a9d9acde6     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует 

**Заголовки ответа**       
Content-Length: 0     
Date: Fri, 16 Jun 2023 09:47:36 GMT     
Server: Kestrel     
Allow: GET, POST     

**Тело ответа** отсутствует

### 86. Проверка эндпоинта PUT​/api​/v1​/Users​/{id} изменение типа значений

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/null

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 415 Unsupported Media Type

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: ab8fbdae-cf13-4881-9708-2a3f38d0d8a4     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует 

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 09:55:41 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
``` 
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",
    "title": "Unsupported Media Type",
    "status": 415,
    "traceId": "00-83f38885ebcbb347b4114112a8b1f347-d7de2f0e0fca4445-00"
}
```

## 87. Проверка эндпоинта PUT​/api​/v1​/Users​/{id} провальный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/22345678987654356789

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 415 Unsupported Media Type

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 2d3a4dd6-cfde-4c53-b76b-58417e99e205     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 10:00:33 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",
    "title": "Unsupported Media Type",
    "status": 415,
    "traceId": "00-7bc3880641ee2e4f91d570bc8f684741-9daa02ad5c9f6c45-00"
}
```

### 88. Проверка эндпоинта PUT​/api​/v1​/Users​/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 405 Method Not Allowed, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: 8a4c5503-8e2c-40cf-9a7a-138aad8b42d6     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```
{
  "id":,
  "userName": "string",
  "password": "string"
}  
```

**Заголовки ответа**      
Content-Length: 0     
Date: Fri, 16 Jun 2023 10:03:52 GMT     
Server: Kestrel     
Allow: GET, POST     

**Тело ответа** отсутствует

### 89. Проверка эндпоинта PUT​/api​/v1​/Users​/{id} провальный (отрицательное значение id)

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/-1

**Ожидаемый результат**     
невозможно исполнить запрос, код состояния 415 Unsupported Media Type

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: c7184d8d-687d-4ec4-8c0a-cc829b6bb90e     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**      
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 10:07:06 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа**
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.13",
    "title": "Unsupported Media Type",
    "status": 415,
    "traceId": "00-e147c64e11c1e448bcac72b7cf9b1fd3-841bb820a2c76846-00"
}
```

### 90. Проверка эндпоинта DELETE​/api​/v1​/Users​/{id} положительный

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/6

**Ожидаемый результат**     
сервер вернет ответ со списком активностей, код состояния - 200 ОК, тело ответа в формате JSON 

**Заголовки запроса**     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: a12f70aa-1d2e-4a8c-99f0-d40b5bea7f66     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса** отсутствует

**Заголовки ответа**     
Content-Length: 0     
Date: Fri, 16 Jun 2023 10:10:23 GMT     
Server: Kestrel     
api-supported-versions: 1.0     

**Тело ответа** отсутствует

### 91. Проверка эндпоинта DELETE​/api​/v1​/Users/{id} пустой запрос

**URL** https://fakerestapi.azurewebsites.net/api/v1/Users/{{}}

**Ожидаемый результат**     
невозможно выполнение запроса, код состояния 400 Bad Request, формат тела ответа JSON

**Заголовки запроса**     
Content-Type: application/json     
User-Agent: PostmanRuntime/7.32.3     
Accept: */*     
Cache-Control: no-cache     
Postman-Token: f29a697a-c066-4b1d-81f0-f8e81ebcb7f1     
Host: fakerestapi.azurewebsites.net     
Accept-Encoding: gzip, deflate, br     
Connection: keep-alive     

**Тело запроса**
```
{
  "id":,
  "userName": "string",
  "password": "string"
}
```

**Заголовки ответа**       
Content-Type: application/problem+json; charset=utf-8     
Date: Fri, 16 Jun 2023 10:13:24 GMT     
Server: Kestrel     
Transfer-Encoding: chunked     

**Тело ответа** 
```
{
    "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "traceId": "00-991a3395aa46294ebf34d989af84009e-db4158ed4b2e7241-00",
    "errors": {
        "id": [
            "The value '{{}}' is not valid."
        ]
    }
}
```





