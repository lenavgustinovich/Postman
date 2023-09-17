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

![Screenshot from 2023-08-14 21-13-28.png](/HW_1_Screenshot/Screenshot%20from%202023-08-14%2021-13-28.png)

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
                              

### Tests:
1. Status code 200
2. 
