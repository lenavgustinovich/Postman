# 1. Need to log in.
POST
http://162.55.220.72:5005/login

login : str (except /)

password : str

The incoming token must be passed to all other requests.
Further all requests require the presence of a token.


![Screenshot from 2023-08-14 21-07-55.png](/HW_1_Screenshot/Screenshot%20from%202023-08-14%2021-07-55.png)

![Screenshot from 2023-08-14 21-13-28.png](/HW_1_Screenshot/Screenshot%20from%202023-08-14%2021-13-28.png)

# 2. Send a request to http://162.55.220.72:5005/user_info

Add parameters of the request (Raw json)

Create json format with this:

`age: int

salary: int

name: str

auth_token`

resp:

`{'start_qa_salary':salary,
 'qa_salary_after_6_months': salary * 2,
 'qa_salary_after_12_months': salary * 2.9,
 'person': {'u_name':[user_name, salary, age],
                                'u_age':age,
                                'u_salary_1.5_year': salary * 4}
                                }`

### 1. Send a request to http://162.55.220.72:5005/user_info
