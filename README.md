# Postman

<details>

  <summary>POSTMAN HW#1</summary>

Создать запросы в Postman.

<b>Protocol:</b>  <code> <b>http</b> </code>

<b>IP:</b> <code> <b>162.55.220.72</b> </code>

<b>Port:</b> <code> <b>5005</b> </code>

---
+ EP_1

<b>Method:</b> <code> <b>GET</b> </code>

<b>EndPoint:</b> <code> <b>/get_method</b> </code>

request url params: 

 name: str

 age: int

response:
``` 
[
    “Str”,
    “Str”
]
```
![EP_1](https://github.com/VictoriaK-QA/Postman/blob/main/Postman_screenshot/EP_1.JPG)

---

+ EP_2

<b>Method:</b> <code> <b>POST</b> </code>

<b>EndPoint:</b> <code> <b>/user_info_3</b> </code>

request form data: 

 name: str

 age: int

 salary: int

response: 
```
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'u_salary_1_5_year': salary * 4}}
```
![EP_2](https://github.com/VictoriaK-QA/Postman/blob/main/Postman_screenshot/EP_2.JPG)

---

+ EP_3


<b>Method:</b> <code> <b>GET</b> </code>

<b>EndPoint:</b> <code> <b>/object_info_1</b> </code>

request url params: 

 name: str

 age: int

 weight: int

response: 
```
{'name': name,
          'age': age,
          'daily_food': weight * 0.012,
          'daily_sleep': weight * 2.5}
```
![EP_3](https://github.com/VictoriaK-QA/Postman/blob/main/Postman_screenshot/EP_3.JPG)

---

+ EP_4

<b>Method:</b> <code> <b>GET</b> </code>

<b>EndPoint:</b> <code> <b>/object_info_2</b> </code>

request url params: 

 name: str

 age: int

 salary: int

response: 
```
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
          }
```
![EP_4](https://github.com/VictoriaK-QA/Postman/blob/main/Postman_screenshot/EP_4.JPG)

---

+ EP_5

<b>Method:</b> <code> <b>GET</b> </code>

<b>EndPoint:</b> <code> <b>/object_info_3</b> </code>

request url params: 

 name: str

 age: int

 salary: int

response: 
```
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'pets': {'cat':{'name':'Sunny',
                                     'age': 3},
                              'dog':{'name':'Luky',
                                     'age': 4}},
                     'u_salary_1_5_year': salary * 4}
          }
```
![EP_5](https://github.com/VictoriaK-QA/Postman/blob/main/Postman_screenshot/EP_5.JPG)

---

+ EP_6

<b>Method:</b> <code> <b>GET</b> </code>

<b>EndPoint:</b> <code> <b>/object_info_4</b> </code>

request url params: 

 name: str

 age: int

 salary: int

response:
``` 
{'name': name,
          'age': int(age),
          'salary': [salary, str(salary * 2), str(salary * 3)]}
```
![EP_6](https://github.com/VictoriaK-QA/Postman/blob/main/Postman_screenshot/EP_6.JPG)

---

+ EP_7

<b>Method:</b> <code> <b>POST</b> </code>

<b>EndPoint:</b> <code> <b>/user_info_2</b> </code>
request form data: 

 name: str

 age: int

 salary: int

response: 
```
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
          }
```
![EP_7](https://github.com/VictoriaK-QA/Postman/blob/main/Postman_screenshot/EP_7.JPG)

</details>

---

<details>

  <summary>POSTMAN HW#2</summary>

:one: http://162.55.220.72:5005/first
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.
```
pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
});
```

---

:two: http://162.55.220.72:5005/user_info_3
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
var jsonData = pm.response.json();
```
4. Проверить, что name в ответе равно name s request (name вбить руками.)
```
var resp_name = jsonData.name;
console.log("resp_name = " + resp_name)
pm.test("NAME_check", function () {
    pm.expect(resp_name).to.eql("Victoria");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками.)
```
var resp_age = jsonData.age;
var resp_age = +resp_age;
console.log("resp_age = " +resp_age)
pm.test("AGE_check", function () {
    pm.expect(resp_age).to.eql(28);
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```
var resp_salary = jsonData.salary;
console.log("resp_salary = " +resp_salary)
pm.test("SALARY_check", function () {
    pm.expect(resp_salary).to.eql(1000);
});
```
7. Спарсить request.
```
var req = request.data;
```
8. Проверить, что name в ответе равно name s request (name забрать из request.)
```
var req_name = req.name;

console.log("resp_name = " + resp_name)
console.log("req_name = " + req_name)

pm.test("Req_Resp_NAME_check", function () {
    pm.expect(resp_name).to.eql(req_name);
});
```
9. Проверить, что age в ответе равно age s request (age забрать из request.)
```
var req_age = req.age;
var req_age = +req_age;

console.log("resp_age = " + resp_age)
console.log("req_age = " + req_age)

pm.test("Req_Resp_AGE_check", function () {
    pm.expect(resp_age).to.eql(req_age);
});
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
var req_salary = req.salary;
var req_salary = +req_salary;

console.log("resp_salary = " + resp_salary)
console.log("req_salary = " + req_salary)

pm.test("Req_Resp_SALARY_check", function () {
    pm.expect(resp_salary).to.eql(req_salary);
});
```
11. Вывести в консоль параметр family из response.
```
var resp_family = jsonData.family
console.log(resp_family)
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```
var resp_u_salary_1_5_year = jsonData.family.u_salary_1_5_year;

var req = request.data;

console.log("resp_u_salary_1_5_year = " + resp_u_salary_1_5_year)

pm.test("Req_Resp_u_salary_1_5_year_check", function () {
    pm.expect(jsonData.family.u_salary_1_5_year).to.eql(req.salary*4);
});
```

---

:three: http://162.55.220.72:5005/object_info_3
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
var resp = pm.response.json();
```
4. Спарсить request.
```
var req = pm.request.url.query.toObject();
console.log("текст");
console.log(req.name);
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Req_Resp_NAME_check", function () {
    pm.expect(resp.name).to.eql(req.name);
});
```
6. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("Req_Resp_AGE_check", function () {
    pm.expect(resp.age).to.eql(req.age);
});
```
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
pm.test("Req_Resp_SALARY_check", function () {
    pm.expect(resp.salary).to.eql(+req.salary);
});
```
8. Вывести в консоль параметр family из response.
```
console.log(resp.family)
```
9. Проверить, что у параметра dog есть параметры name.
```
pm.test("dog_parameter_check_name", function () {
    pm.expect(resp.family.pets.dog).to.have.property("name");
});
```
10. Проверить, что у параметра dog есть параметры age.
```
pm.test("dog_parameter_check_age", function () {
    pm.expect(resp.family.pets.dog).to.have.property("age");
});
```
11. Проверить, что параметр name имеет значение Luky.
```
console.log(resp.family.pets.dog.name)

pm.test("dog_name_Luky", function () {
    pm.expect(resp.family.pets.dog).to.have.property("name");
});
```
12. Проверить, что параметр age имеет значение 4.
```
console.log(resp.family.pets.dog.age)

pm.test("dog_age_4", function () {
    pm.expect(resp.family.pets.dog.age).to.eql(4);
});
```

---

:four: http://162.55.220.72:5005/object_info_4
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
var resp = pm.response.json();
```
4. Спарсить request.
```
var req = pm.request.url.query.toObject();
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Req_Resp_NAME_check", function () {
    pm.expect(resp.name).to.eql(req.name);
});
```
6. Проверить, что age в ответе равно age из request (age забрать из request.)
```
pm.test("Req_Resp_AGE_check", function () {
    pm.expect(resp.age).to.eql(+req.age);
});
```
7. Вывести в консоль параметр salary из request.
```
console.log(req.salary)
```
8. Вывести в консоль параметр salary из response.
```
console.log(resp.salary)
```
9. Вывести в консоль 0-й элемент параметра salary из response.
```
console.log(resp.salary[0])
```
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```
console.log(resp.salary[1])
```
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```
console.log(resp.salary[2])
```
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```
pm.test("Req_Resp_0_SALARY_check", function () {
    pm.expect(+resp.salary[0]).to.eql(+req.salary);
});
```
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```
pm.test("Req_Resp_1_SALARY_check", function () {
    pm.expect(+resp.salary[1]).to.eql(+req.salary*2);
});
```
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```
pm.test("Req_Resp_2_SALARY_check", function () {
    pm.expect(+resp.salary[2]).to.eql(+req.salary*3);
});
```
15. Создать в окружении переменную name
```
pm.environment.get("name");
```
16. Создать в окружении переменную age
```
pm.environment.get("age");
```
17. Создать в окружении переменную salary
```
pm.environment.get("salary");
```
18. Передать в окружение переменную name
```
var jsonData = pm.response.json();
var resp_name = jsonData.name
console.log(resp_name)

pm.environment.set("name", resp_name);
```
19. Передать в окружение переменную age
```
var resp_age = jsonData.age
console.log(resp_age)

pm.environment.set("age", resp_age);
```
20. Передать в окружение переменную salary
```
var resp_salary = jsonData.salary
console.log(resp_salary)

pm.environment.set("salary", resp_salary[1]);
```
21. :star::star::star: Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```
console.log("цикл");
for (var s in resp_salary){
    console.log(resp_salary[s])
};
```

---

:five: http://162.55.220.72:5005/user_info_2
1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name
4. Отправить запрос.
5. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
6. Спарсить response body в json.
```
var resp = pm.response.json();
```
7. Спарсить request.
```
var req = request.data;
```
8. Проверить, что json response имеет параметр start_qa_salary
```
pm.test("json_response_check_start_qa_salary", function () {
    pm.expect(resp).to.have.property("start_qa_salary");
});
```
9. Проверить, что json response имеет параметр qa_salary_after_6_months
```
pm.test("json_response_qa_salary_after_6_months", function () {
    pm.expect(resp).to.have.property("qa_salary_after_6_months");
});
```
10. Проверить, что json response имеет параметр qa_salary_after_12_months
```
pm.test("json_response_qa_salary_after_12_months", function () {
    pm.expect(resp).to.have.property("qa_salary_after_12_months");
});
```
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```
pm.test("json_response_qa_salary_after_1.5_year", function () {
    pm.expect(resp).to.have.property("qa_salary_after_1.5_year");
});
```
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```
pm.test("json_response_qa_salary_after_3.5_years", function () {
    pm.expect(resp).to.have.property("qa_salary_after_3.5_years");
});
```
13. Проверить, что json response имеет параметр person
```
pm.test("json_response_person", function () {
    pm.expect(resp).to.have.property("person");
});
```
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```
pm.test("Req_Resp_START_SALARY_check", function () {
    pm.expect(resp.start_qa_salary).to.eql(+req.salary);
});
```
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```
pm.test("Req_Resp_6_SALARY_check", function () {
    pm.expect(resp.qa_salary_after_6_months).to.eql(+req.salary*2);
});
```
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```
pm.test("Req_Resp_12_SALARY_check", function () {
    pm.expect(resp.qa_salary_after_12_months).to.eql(+req.salary*2.7);
});
```
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```
pm.test("Req_Resp_1.5year_SALARY_check", function () {
    pm.expect(resp['qa_salary_after_1.5_year']).to.eql(+req.salary*3.3);
});
```
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```
pm.test("Req_Resp_3.5years_SALARY_check", function () {
    pm.expect(resp['qa_salary_after_3.5_years']).to.eql(+req.salary*3.8);
});
```
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```
pm.test("Req_Resp_person1_SALARY_check", function () {
    pm.expect(resp.person.u_name[1]).to.eql(+req.salary);
});
```
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```
pm.test("Req_Resp_personage_SALARY_check", function () {
    pm.expect(resp.person.u_age).to.eql(+req.age);
});
```
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```
pm.test("Req_Resp_5_years_SALARY_check", function () {
    pm.expect(resp.person.u_salary_5_years).to.eql(+req.salary*4.2);
});
```
22. :star::star::star: Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```
console.log("цикл");
for (var p in resp.person){
    console.log(resp.person[p])
};
```

</details>

---

<details>

  <summary>POSTMAN HW#3</summary>

:one: Необходимо залогиниться

POST
http://162.55.220.72:5005/login

login : str (кроме /)
password : str

Приходящий токен необходимо передать во все остальные запросы.
```
var jsonData = pm.response.json();
var resp_token = jsonData.token
console.log(resp_token)

pm.environment.set("token", resp_token);
```
---
дальше все запросы требуют наличие токена

---

:two: http://162.55.220.72:5005/user_info

req. (RAW JSON)

POST

age: int

salary: int

name: str

auth_token


Resp.
```
{'start_qa_salary':salary,
 'qa_salary_after_6_months': salary * 2,
 'qa_salary_after_12_months': salary * 2.9,
 'person': {'u_name':[user_name, salary, age],
                                'u_age':age,
                                'u_salary_1.5_year': salary * 4}
                                }
```

Тесты:
1. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. Проверка структуры json в ответе.
```
var schema = {
    "type": "object",
    "default": {},
    "title": "Root Schema",
    "required": [
        "person",
        "qa_salary_after_12_months",
        "qa_salary_after_6_months",
        "start_qa_salary"
    ],
    "properties": {
        "person": {
            "type": "object",
            "default": {},
            "title": "The person Schema",
            "required": [
                "u_age",
                "u_name",
                "u_salary_1_5_year"
            ],
            "properties": {
                "u_age": {
                    "type": "integer",
                    "default": 0,
                    "title": "The u_age Schema",
                    "examples": [
                        28
                    ]
                },
                "u_name": {
                    "type": "array",
                    "default": [],
                    "title": "The u_name Schema",
                    "items": {
                        "anyOf": [{
                            "type": "string",
                            "default": "",
                            "title": "A Schema",
                            "examples": [
                                "Victoria"
                            ]
                        },
                        {
                            "type": "integer",
                            "title": "A Schema",
                            "examples": [
                                1000,
                                28
                            ]
                        }]
                    },
                    "examples": [
                        ["Victoria",
                            1000,
                            28
                        ]
                    ]
                },
                "u_salary_1_5_year": {
                    "type": "integer",
                    "default": 0,
                    "title": "The u_salary_1_5_year Schema",
                    "examples": [
                        4000
                    ]
                }
            },
            "examples": [{
                "u_age": 28,
                "u_name": [
                    "Victoria",
                    1000,
                    28
                ],
                "u_salary_1_5_year": 4000
            }]
        },
        "qa_salary_after_12_months": {
            "type": "number",
            "default": 0.0,
            "title": "The qa_salary_after_12_months Schema",
            "examples": [
                2900.0
            ]
        },
        "qa_salary_after_6_months": {
            "type": "integer",
            "default": 0,
            "title": "The qa_salary_after_6_months Schema",
            "examples": [
                2000
            ]
        },
        "start_qa_salary": {
            "type": "integer",
            "default": 0,
            "title": "The start_qa_salary Schema",
            "examples": [
                1000
            ]
        }
    },
    "examples": [{
        "person": {
            "u_age": 28,
            "u_name": [
                "Victoria",
                1000,
                28
            ],
            "u_salary_1_5_year": 4000
        },
        "qa_salary_after_12_months": 2900.0,
        "qa_salary_after_6_months": 2000,
        "start_qa_salary": 1000
    }]
}
pm.test("Проверка структуры json в ответе", function () {
    pm.response.to.have.jsonSchema(schema);
});
```
3. В ответе указаны коэффициенты умножения salary, напишите тесты по проверке правильности результата перемножения на коэффициент.
```
var resp = pm.response.json();
var req = request.data;

pm.test("SALARY_6_months", function () {
    pm.expect(+resp.qa_salary_after_6_months).to.eql(+request.salary*2);
});

pm.test("SALARY_12_months", function () {
    pm.expect(+resp.qa_salary_after_12_months).to.eql(+request.salary*2.9);
});

pm.test("SALARY_1_5_year", function () {
    pm.expect(+resp.u_salary_1_5_year).to.eql(+request.salary*4);
});
```
4. Достать значение из поля 'u_salary_1.5_year' и передать в поле salary запроса http://162.55.220.72:5005/get_test_user
```
var resp_salary_1_5_year = JSON.parse(resp.person.u_salary_1_5_year);
console.log(resp_salary_1_5_year)
pm.environment.get("salary_1_5");
pm.environment.set("salary_1_5", resp_salary_1_5_year);
```

---

:three: http://162.55.220.72:5005/new_data

req.

POST

age: int

salary: int

name: str

auth_token

Resp.
```
{'name':name,
  'age': int(age),
  'salary': [salary, str(salary*2), str(salary*3)]}
```

Тесты:
1. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. Проверка структуры json в ответе.
```
var schema = {
    "type": "object",
    "default": {},
    "title": "Root Schema",
    "required": [
        "age",
        "name",
        "salary"
    ],
    "properties": {
        "age": {
            "type": "integer",
            "default": 0,
            "title": "The age Schema",
            "examples": [
                28
            ]
        },
        "name": {
            "type": "string",
            "default": "",
            "title": "The name Schema",
            "examples": [
                "Victoria"
            ]
        },
        "salary": {
            "type": "array",
            "default": [],
            "title": "The salary Schema",
            "items": {
                "anyOf": [{
                    "type": "integer",
                    "default": 0,
                    "title": "A Schema",
                    "examples": [
                        1000
                    ]
                },
                {
                    "type": "string",
                    "title": "A Schema",
                    "examples": [
                        "2000",
                        "3000"
                    ]
                }]
            },
            "examples": [
                [1000,
                    "2000",
                    "3000"
                ]
            ]
        }
    },
    "examples": [{
        "age": 28,
        "name": "Victoria",
        "salary": [
            1000,
            "2000",
            "3000"
        ]
    }]
}

pm.test("Проверка структуры json в ответе", function () {
    pm.response.to.have.jsonSchema(schema);
});
```
3. В ответе указаны коэффициенты умножения salary, напишите тесты по проверке правильности результата перемножения на коэффициент.
```
// Спарсить response body в json
var resp = pm.response.json();
// // Спарсить request.
var req = request.data;

pm.test("SALARY[0]", function () {
    pm.expect(+resp.salary[0]).to.eql(+req.salary);
});

pm.test("SALARY[1]", function () {
    pm.expect(+resp.salary[1]).to.eql(+req.salary*2);
});

pm.test("SALARY[2]", function () {
    pm.expect(+resp.salary[2]).to.eql(+req.salary*3);
});
```
4. проверить, что 2-й элемент массива salary больше 1-го и 0-го
```
pm.test("salary2 > salary1 && salary0", function () {
    const salCheck = resp.salary[2] > resp.salary[1] && resp.salary[2] > resp.salary[0]
    pm.expect(salCheck).to.be.true
});
```
---

:four: http://162.55.220.72:5005/test_pet_info

req.

POST

age: int

weight: int

name: str

auth_token


Resp.
```
{'name': name,
 'age': age,
 'daily_food':weight * 0.012,
 'daily_sleep': weight * 2.5}
```

Тесты:
1. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. Проверка структуры json в ответе.
```
var schema = {
    "type": "object",
    "default": {},
    "title": "Root Schema",
    "required": [
        "age",
        "daily_food",
        "daily_sleep",
        "name"
    ],
    "properties": {
        "age": {
            "type": "integer",
            "default": 0,
            "title": "The age Schema",
            "examples": [
                28
            ]
        },
        "daily_food": {
            "type": "number",
            "default": 0.0,
            "title": "The daily_food Schema",
            "examples": [
                0.6
            ]
        },
        "daily_sleep": {
            "type": "number",
            "default": 0.0,
            "title": "The daily_sleep Schema",
            "examples": [
                125.0
            ]
        },
        "name": {
            "type": "string",
            "default": "",
            "title": "The name Schema",
            "examples": [
                "Victoria"
            ]
        }
    },
    "examples": [{
        "age": 28,
        "daily_food": 0.6,
        "daily_sleep": 125.0,
        "name": "Victoria"
    }]
}

pm.test("Проверка структуры json в ответе", function () {
    pm.response.to.have.jsonSchema(schema);
});
```
3. В ответе указаны коэффициенты умножения weight, напишите тесты по проверке правильности результата перемножения на коэффициент.
```
// Спарсить response body в json
var resp = pm.response.json();
// // Спарсить request.
var req = request.data;

pm.test("WEIGHT_1", function () {
    pm.expect(resp.daily_food).to.eql(req.weight*0.012);
});

pm.test("WEIGHT_2", function () {
    pm.expect(resp.daily_sleep).to.eql(req.weight*2.5);
});
```
---

:five: http://162.55.220.72:5005/get_test_user

req.

POST

age: int

salary: int

name: str

auth_token

Resp.
```
{'name': name,
 'age':age,
 'salary': salary,
 'family':{'children':[['Alex', 24],['Kate', 12]],
 'u_salary_1.5_year': salary * 4}
  }
```

Тесты:
1. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
2. Проверка структуры json в ответе.
```
var schema = {
    "type": "object",
    "default": {},
    "title": "Root Schema",
    "required": [
        "age",
        "family",
        "name",
        "salary"
    ],
    "properties": {
        "age": {
            "type": "string",
            "default": "",
            "title": "The age Schema",
            "examples": [
                "28"
            ]
        },
        "family": {
            "type": "object",
            "default": {},
            "title": "The family Schema",
            "required": [
                "children",
                "u_salary_1_5_year"
            ],
            "properties": {
                "children": {
                    "type": "array",
                    "default": [],
                    "title": "The children Schema",
                    "items": {
                        "type": "array",
                        "title": "A Schema",
                        "items": {
                            "anyOf": [{
                                "type": "string",
                                "title": "A Schema",
                                "examples": [
                                    "Alex",
                                    "Kate"
                                ]
                            },
                            {
                                "type": "integer",
                                "title": "A Schema",
                                "examples": [
                                    24,
                                    12
                                ]
                            }]
                        },
                        "examples": [
                            ["Alex",
                                24
                            ],
                            ["Kate",
                                12
                            ]
                        ]
                    },
                    "examples": [
                        [
                            ["Alex",
                                24
                            ],
                            ["Kate",
                                12
                            ]
                        ]
                    ]
                },
                "u_salary_1_5_year": {
                    "type": "integer",
                    "default": 0,
                    "title": "The u_salary_1_5_year Schema",
                    "examples": [
                        4000
                    ]
                }
            },
            "examples": [{
                "children": [
                    ["Alex",
                        24
                    ],
                    ["Kate",
                        12
                    ]
                ],
                "u_salary_1_5_year": 4000
            }]
        },
        "name": {
            "type": "string",
            "default": "",
            "title": "The name Schema",
            "examples": [
                "Victoria"
            ]
        },
        "salary": {
            "type": "integer",
            "default": 0,
            "title": "The salary Schema",
            "examples": [
                1000
            ]
        }
    },
    "examples": [{
        "age": "28",
        "family": {
            "children": [
                ["Alex",
                    24
                ],
                ["Kate",
                    12
                ]
            ],
            "u_salary_1_5_year": 4000
        },
        "name": "Victoria",
        "salary": 1000
    }]
}

pm.test("Проверка структуры json в ответе", function () {
    pm.response.to.have.jsonSchema(schema);
});
```
3. Проверить что занчение поля name = значению переменной name из окружения
```
// Спарсить response body в json
var resp = pm.response.json();
console.log(pm.environment.get("name"))
pm.test("enviroment_name", function () {
    pm.expect(pm.environment.get("name")).to.eql(resp.name);
});
```
4. Проверить что занчение поля age в ответе соответсвует отправленному в запросе значению поля age
```
// // Спарсить request.
var req = request.data;

pm.test("Req_Resp_AGE_check", function () {
    pm.expect(resp.age).to.eql(req.age);
});
```
---

:six: http://162.55.220.72:5005/currency

req.
POST
auth_token
Resp. Передаётся список массив объектов.
```
[
{"Cur_Abbreviation": str,
 "Cur_ID": int,
 "Cur_Name": str
}
…
{"Cur_Abbreviation": str,
 "Cur_ID": int,
 "Cur_Name": str
}
]
```

Тесты:
1. Можете взять любой объект из присланного списка, используйте js random.
В объекте возьмите Cur_ID и передать через окружение в следующий запрос.

---

:seven: http://162.55.220.72:5005/curr_byn

req.

POST

auth_token

curr_code: int

Resp.
```
{
    "Cur_Abbreviation": str
    "Cur_ID": int,
    "Cur_Name": str,
    "Cur_OfficialRate": float,
    "Cur_Scale": int,
    "Date": str
}
```

Тесты:
1. Статус код 200
2. Проверка структуры json в ответе.

---
:star: :star: :star:
1. получить список валют
2. итерировать список валют
3. в каждой итерации отправлять запрос на сервер для получения курса каждой валюты
4. если возвращается 500 код, переходим к следующей итреации
5. если получаем 200 код, проверяем response json на наличие поля "Cur_OfficialRate"
6. если поле есть, пишем в консоль инфу про фалюту в виде response
```
{
    "Cur_Abbreviation": str
    "Cur_ID": int,
    "Cur_Name": str,
    "Cur_OfficialRate": float,
    "Cur_Scale": int,
    "Date": str
}
```
7. переходим к следующей итерации


</details>

---


<details>

  <summary>МЕТОДЫ HTTP ЗАПРОСА</summary>
  
| МЕТОДЫ |  ОПИСАНИЕ | 
| :-----: |:-----|
`GET` | **запрашивает представление ресурса (показать/отправить/изменить)**
`HEAD` | **запрашивает ресурс так же, как и метод GET, но без тела ответа**
`POST` | **создает новый ресурс из переданных данных в запросе**
`PUT` | **заменяет все текущие представления ресурса данными запроса**
`PATCH` | **используется для частичного изменения ресурса**
`DELETE` | **удаляет указанный ресурс**
`CONNECT` | **устанавливает "туннель" к серверу, определённому по ресурсу**
`OPTIONS` | **используется для описания параметров соединения с ресурсом**
`TRACE` | **выполняет вызов возвращаемого тестового сообщения с ресурса**


</details>

---

<details>

  <summary>КОДЫ ОТВЕТА HTTP</summary>
  
| КОДЫ | ОПИСАНИЕ | ПРИМЕР |
| :-----: |:-----:| :----- |
| **1хх**  | Информационные сообщения | `102` — запрос принят, но обработка ещё не завершена |
| **2хх**   | Сообщения об успехе      | `200` — ОК, запрос обработан успешно |
| **3хх**   | Перенаправление          | `302` — запрошенный ресурс временно доступен по другому адресу |
| **4хх**   | Клиентские ошибки        | `403` Forbidden — у клиента недостаточно прав, чтобы получить доступ к данному ресурсу |
| **5хх**   | Ошибки сервера           | `500` Internal Server Error — внутренняя ошибка сервера |

  
</details>

---