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
   
### 5. Test that salary in the response is equal to salary is request (tnter manually)
    pm.test("Check test salary", function () {
    
    pm.expect(RespData.salary).to.eql(70);
    });
![2023-06-05 20-58-02.png](/HW_1_Screenshot/2023-06-05%2020-58-02.png) 

