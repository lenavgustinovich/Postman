# Postman HW_2
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
#
#
### 1. Send a request `http://162.55.220.72:5005/user_info_3`
### 2. Status code 200
`pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});`
### 3. Parse response body to json.
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