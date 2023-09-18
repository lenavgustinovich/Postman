# 1. Необходимо залогиниться.
POST
http://162.55.220.72:5005/login

login : str (except /)

password : str

Приходящий токен необходимо передать во все остальные запросы.

---
1. Создаем новый пост запрос http://162.55.220.72:5005/login
2. В body form-data прописываем: login-Elena, 
password-123
3. Отправляем запрос и получаем в ответе token



![Screenshot from 2023-08-14 21-07-55.png](/HW_1_Screenshot/Screenshot%20from%202023-08-14%2021-07-55.png)
4. Добавляем переменную token в окружение, как здесь:

![Screenshot from 2023-08-14 21-13-28.png](/HW_1_Screenshot/21-13-28.png)

---

# 2. Отправить запрос на  http://162.55.220.72:5005/user_info

``` 
req. (RAW JSON) 

POST

age: int

salary: int

name: str

auth_token
 

resp:

{'start_qa_salary':salary,
 'qa_salary_after_6_months': salary * 2,
 'qa_salary_after_12_months': salary * 2.9,
 'person': {'u_name':[user_name, salary, age],
                                'u_age':age,
                                'u_salary_1.5_year': salary * 4}
                                }
```
---

---
1. Создаем новый пост запрос http://162.55.220.72:5005/user_info
2. В body raw вставляем json:
```
{
     "age": 30,
     "salary": 70,
     "name": "Lena",
     "auth_token": "{{token}}"
}
```
3. Отправляем запрос
---
Тесты:
1. ```Статус код 200```
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. ```Проверка структуры json в ответе```
```
const schema = {
    "type": "object",
    "required": [
        "start_qa_salary",
        "qa_salary_after_6_months",
        "qa_salary_after_12_months",
        "person"
    ],
    "properties": {
        "start_qa_salary": {
            "type": "integer"
        },
        "qa_salary_after_6_months": {
            "type": "integer"
        },
        "qa_salary_after_12_months": {
            "type": "number"
        },
        "person": {
            "type": "object",
            "required": [
                "u_name",
                "u_age",
                "u_salary_1_5_year"
            ],
            "properties": {
                "u_name": {
                    "type": "array",
                    "minItems": 3,
                    "maxItems": 3,
                    "items": [
                        {
                            "type": "string"
                        },
                        {
                            "type": "integer"
                        },
                        {
                            "type": "integer"
                        }
                    ]
                },
                "u_age": {
                    "type": "integer",
                    "minimum": 0
                },
                "u_salary_1_5_year": {
                    "type": "integer"
                }
            }
        }
    }
};

pm.test("Validating schema", () => {
    pm.response.to.have.jsonSchema(schema);
});
```
3. ```В ответе указаны коэффициенты умножения salary, напишите тесты по проверке правильности результата перемножения на коэффициент```
![18-36-27.png](/HW_1_Screenshot/18-36-27.png)

4. ```Достать значение из поля 'u_salary_1.5_year' и передать в поле salary запроса http://162.55.220.72:5005/get_test_user```
![18-41-26.png](/HW_1_Screenshot/18-41-26.png)
---
# 3.http://162.55.220.72:5005/new_data
```
req.
POST
age: int
salary: int
name: str
auth_token

Resp.
{'name':name,
  'age': int(age),
  'salary': [salary, str(salary*2), str(salary*3)]}
```
---
Тесты:
1. ```Статус код 200```
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. ```Проверка структуры json в ответе```
```
const schema = {
    "type": "object",
     "required": [
    "age",
    "name",
    "salary"
  ],
     "properties": {
         "age":{
             "type": "integer"
         },
         "name": {
             "type": "string"
         },
         "salary": {
             "type": "array",
         "items":[
             {
                            "type": "integer"
                        },
                        {
                            "type": "string"
                        },
                        {
                            "type": "string"
                        }

         ] }
     }
}

pm.test("Validating schema", () => {
    pm.response.to.have.jsonSchema(schema);
});    
```
3. ```В ответе указаны коэффициенты умножения salary, напишите тесты по проверке правильности результата перемножения на коэффициент```
![8-54-29.png](/HW_1_Screenshot/8-54-29.png)
4. ``` Проверить, что 2-й элемент массива salary больше 1-го и 0-го```
![54.png](/HW_1_Screenshot/54.png)

# 4.http://162.55.220.72:5005/test_pet_info

```
req.
POST
age: int
weight: int
name: str
auth_token


Resp.
{'name': name,
 'age': age,
 'daily_food':weight * 0.012,
 'daily_sleep': weight * 2.5}
```
---
Тесты:
1. ```Статус код 200```
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. ```Проверка структуры json в ответе```
```
const schema = {
 "type": "object",
   "properties":{
     "age":{
         "type": "integer"
         },
     "daily_food":{
        "type": "number"
    },
    "daily_sleep": {
        "type": "number"
    },
    "name": {
        "type": "string"
    }
   },
     "required": [
         "age",
    "daily_food",
    "daily_sleep",
    "name"
  ]

}

pm.test("Validating schema", () => {
    pm.response.to.have.jsonSchema(schema);
}); 
```
3. ```В ответе указаны коэффициенты умножения weight, напишите тесты по проверке правильности результата перемножения на коэффициент```
![9-15-34.png](/HW_1_Screenshot/9-15-34.png)

# 5. http://162.55.220.72:5005/get_test_user
```
req.
POST
age: int
salary: int
name: str
auth_token

Resp.
{'name': name,
 'age':age,
 'salary': salary,
 'family':{'children':[['Alex', 24],['Kate', 12]],
 'u_salary_1.5_year': salary * 4}
  }
```
---
Тесты:
1. ```Статус код 200```
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. ```Проверка структуры json в ответе```
3. ```Проверить что занчение поля name = значению переменной name из окружения```
![9-20-26.png](/HW_1_Screenshot/9-20-26.png)
4. ```Проверить что занчение поля age в ответе соответсвует отправленному в запросе значению поля age```
![18 12-29-25.png](/HW_1_Screenshot/18%2012-29-25.png)


