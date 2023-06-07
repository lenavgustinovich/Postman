# Postman HW_2
# 1.`Get` method, EndPoint:`/first`
### 1. Send a request `http://162.55.220.72:5005/first`
### 2. Status code 200
`pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});`
### 3. Test that there is a correct string in the body
`pm.test("Body string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
});`
![q.png](/HW_1_Screenshot/q.png) 

# 2. `Post` method, EndPoint: `/user_info_3`
### 1. Send a request `http://162.55.220.72:5005/user_info_3`
### 2. Status code 200
`pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});`
### 3. Parsing response body to json.
`var RespData = pm.response.json();`
### 4. Test that name in the response is equal to name is request (tnter manually)
    pm.test("Check test name", function () {
   
    pm.expect(RespData.name).to.eql("Lena");
    });
### 5. Test that age in the response is equal to age is request (tnter manually)
    pm.test("Check test name", function () {
   
    pm.expect(RespData.name).to.eql("Lena");
    });
   
### 6. Test that salary in the response is equal to salary is request (tnter manually)
    pm.test("Check test salary", function () {
    
    pm.expect(RespData.salary).to.eql(70);
    });
![2023-06-05 20-58-02.png](/HW_1_Screenshot/2023-06-05%2020-58-02.png) 

### 7. Parsing request.
`var Req = request.data;`
![2023-06-05 21-17-27.png](/HW_1_Screenshot/2023-06-05%2021-17-27.png) 

### 8. Test that name in the response is equal to name is request (take name from request)
    pm.test("Check name resp to eql req", function () {
  
    pm.expect(RespData.name).to.eql(Req.name);
    });
 ### 9. Test that age in the response is equal to age is request (take name from request)   
    pm.test("Check age resp to eql req", function () {
  

    pm.expect(RespData.age).to.eql(Req.age);
    });
 ### 10. Test that salary in the response is equal to salary is request (take name from request)    
     pm.test("Check salary resp to eql req", function () {
  
    pm.expect(RespData.salary).to.eql(Number(Req.salary));
    });
![ 2023-06-05 21-59-11.png](/HW_1_Screenshot/2023-06-05%2021-59-11.png) 

### 11. Output parameter family to console from response
`console.log(RespData.family) `
### 12. Test that u_salary_1_5_year  in the response is equal to salary*4 is request (take name from request) 
    pm.test("Check salary resp_1_5 to eql req*4", function () {
  
    pm.expect(RespData.family.u_salary_1_5_year).to.eql(Req.salary * 4);
    });
![2023-06-05 22-08-06.png](/HW_1_Screenshot/2023-06-05%2022-08-06.png) 

 # 3. `Get` method, EndPoint:` /object_info_3`
### 1. Send a request ` http://162.55.220.72:5005/object_info_3?name=Lena&age=30&salary=70 `
### 2. Status code 200
    pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
    });
![6-06 23-26-50.png](/HW_1_Screenshot/6-06%2023-26-50.png)
### 3. Parsing response body to json.
`var Resp = pm.response.json();`
### 4. Parsing request.
`var Req = pm.request.url.query.toObject()`
### 5. Test that name in the response body is equal to name in request ( take name from request)
    pm.test("Check resp name=req name", function () {
   
    pm.expect(Resp.name).to.eql(Req.name);
    });
### 6.  Test that age in the response body is equal to age in request ( take name from request)       
    pm.test("Check resp age-req age ", function () {
   
    pm.expect(Resp.age).to.eql(Req.age);
    });
### 7.  Test that salary in the response body is equal to salary in request ( take name from request)    
    pm.test("Check resp salary=req salary", function () {
   
    pm.expect(Resp.salary).to.eql(Number(Req.salary));
    });   

 ![3-06-0623-36-53.png](/HW_1_Screenshot/3-06-0623-36-53.png)

 ### 8. Output parameter family to console from response.
 `console.log(Resp.family)`
 ### 9.  Test that parameter dog has parameter name.
    pm.test("Check the dog have name ", function () {
   
    pm.expect(Resp.family.pets.dog).to.property("name");
    });
### 10. Test that parameter dog has parameter age.
    pm.test("Check the dog have age ", function () {
   
    pm.expect(Resp.family.pets.dog).to.property("age");
    });
### 11. Test that parameter name has a value Luky.
    pm.test("Check the dog_name=Luky ", function () {
   
    pm.expect(Resp.family.pets.dog.name).to.eql("Luky");
    });  
### 12. Test that parameter age has a value 4.      
    pm.test("Check the dog_age=4 ", function () {
   
    pm.expect(Resp.family.pets.dog.age).to.eql(4);
    }); 
![23-06-06 23-47-55.png](/HW_1_Screenshot/23-06-06%2023-47-55.png)     

# 4. `Get` method, EndPoint: `/object_info_4`
### 1. Send a request ` hhttp://162.55.220.72:5005/object_info_4?name=Lena&age=30&salary=70 `
### 2. Status code 200
    pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
    });
### 3. Parsing response body в json.
`var Resp = pm.response.json();`
### 4. Parsing request.
 `var Req = pm.request.url.query.toObject()`    
 ![14-56-05.png](/HW_1_Screenshot/14-56-05.png) 
### 5. Test that name in the response body is equal to name in request ( take name from request)
    pm.test("Check resp.name=req.name", function () {
  
    pm.expect(Resp.name).to.eql(Req.name);
    });
### 6. Test that age in the response body is equal to age in request ( take name from request) 
    pm.test("Check resp.age=req.age", function () {
  
    pm.expect(Resp.age).to.eql(Number(Req.age));
    });  
![15-00-25.png](/HW_1_Screenshot/15-00-25.png)   
### 7.  Output parameter salary to console from request.
`console.log(Req.salary) `
### 8.  Output parameter salary to console from response.
`console.log(Resp.salary) `
### 9.  Output 0 element of parameter salary to console from response.
`console.log(Resp.salary[0]) `
### 10. Output 1 element of parameter salary to console from response.
`console.log(Resp.salary[1])`
### 11. Output 2 element of parameter salary to console from response.
` console.log(Resp.salary[2])`
### 12. Test that 0 element of parameter salary is equal to salary in request(take salary from request)
    pm.test("Check resp.[0]=req.salary", function () {
   
    pm.expect(Resp.salary[0]).to.eql(Number(Req.salary));
    });
### 13. Test that 1 element of parameter salary is equal to salary*2 in request(take salary from request)   
    pm.test("Check resp.[1]=req.salary*2", function () {
  
    pm.expect(Resp.salary[1]).to.eql(String(Req.salary * 2));
    });
### 14. Test that 2 element of parameter salary is equal to salary*3 in request(take salary from request)      
    pm.test("Check resp.[2]=req.salary*3", function () {
  
    pm.expect(Resp.salary[2]).to.eql(String(Req.salary * 3));
    });
