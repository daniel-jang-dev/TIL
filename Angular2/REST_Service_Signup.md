##Client-side

1. signup.component.ts 
  * collect user's input and validate
  * declare member object
  * calls apiService.signup(member)
  
2. api.service.ts
  * stringfy member object
  * sends HTTP POST request to 'join/create'

##Server-side

1. join.js
  * extract request and declare member object (Member schema)
  * check email exists(using db.js)
    * If exists, send error response
    * Else query INSERT statement
  * return response
