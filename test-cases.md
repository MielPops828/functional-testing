# TC-001

Название: Проверка успешного получения статуса продукта;
Предусловия:
- productId существует;
- есть authToken из 16 символов.
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678;
Ожидаемый результат:
- получен http-код: 200;
- получен ответ в json формате: { "productStatus": 0 или 1 }.
Статус: -
Приоритет: High

# TC-002

Название: Отправка запроса без authToken;
Предусловия:
- валидный productId существует;
Шаги:
1. отправить GET запрос: /products/12/status;
Ожидаемый результат:
- получен http-код: 401.
Статус: -
Приоритет: High

# TC-003

Название: Отправка запроса c указанием невалидного productId;
Шаги:
1. отправить GET запрос: /products/prod123/status?authToken=abcd123qwert5678;
Ожидаемый результат:
- получен http-код: 500.
- получен ответ в json формате: { "errorMessage": ...}.
Статус: -
Приоритет: High

# TC-004

Название: Отправка запроса c указанием невалидного токена;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=qwerty123;
Ожидаемый результат:
- получен http-код: 401.
Статус: -
Приоритет: High

# TC-005

Название: Отправка запроса c указанием recalculate=true;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=true;
Ожидаемый результат:
- получен http-код: 200;
- получен ответ в json формате: { "productStatus": 0 или 1}
Статус: -
Приоритет: High

# TC-006

Название: Отправка запроса c указанием невалидного recalculate;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=abc;
Ожидаемый результат:
- получен http-код: 200 или 500;
- получен ответ в формате json {"productStatus": 0 или 1} или {"errorMessage": ...}
Статус: -
Приоритет: High

# TC-007

Название: Отправка запроса c указанием recalculate=null;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=null;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в json формате: { "productStatus": 0 или 1}
Статус: -
Приоритет: High

# TC-008

Название: Отправка запроса c указанием невалидного owner;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&owner=123;
Ожидаемый результат:
- получен http-код: 200 или 500;
- получен ответ в формате json {"productStatus": 0 или 1} или {"errorMessage": ...}
Статус: -
Приоритет: High

# TC-009

Название: Отправка запроса c указанием owner = Создатель;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&owner=Создатель;
Ожидаемый результат:
- получен http-код: 200;
- получен ответ в json формате: { "productStatus": 0 или 1}
Статус: -
Приоритет: High

# TC-010

Название: Отправка запроса c указанием owner = null;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&owner=null;
Ожидаемый результат:
- получен http-код: 200;
- получен ответ в json формате: { "productStatus": 0 или 1}
Статус: -
Приоритет: High

# TC-011

Название: Отправка запроса c указанием region = Северо-Запад;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&region=Северо-Запад;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в json формате: { "productStatus": 0 или 1}
Статус: -
Приоритет: High

# TC-012

Название: Отправка запроса c указанием невалидного region;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&region=123;
Ожидаемый результат:
- получен http-код: 200 или 500.
- получен ответ в формате json {"productStatus": 0 или 1} или {"errorMessage": ...}
Статус: -
Приоритет: High


# TC-013

Название: Отправка запроса c указанием всех параметров;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=true&owner=Создатель&region=Северо-Запад;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в json формате: { "productStatus": 0 или 1}
Статус: -
Приоритет: High


# TC-014

Название: Отправка запроса c передачей пустых параметров;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=&owner=&region=;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в json формате: { "productStatus": 0 или 1}
Статус: -
Приоритет: High


# TC-015

Название: Отправка запроса c передачей SQL-инъекции;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&owner=' OR 1=1 --;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в json формате: { "productStatus": 0 или 1}
- API не падает;
- нет утечки данных.
Статус: -
Приоритет: High


# TC-016

Название: Отправка запроса c передачей authToken длиной 15 символов;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert567;
Ожидаемый результат:
- получен http-код: 401.
Статус: -
Приоритет: High


# TC-017

Название: Отправка запроса c передачей authToken длиной 17 символов;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert56788;
Ожидаемый результат:
- получен http-код: 401.
Статус: -
Приоритет: High


# TC-018

Название: Отправка запроса c передачей authToken со спецсимволами;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123!@#$%^&*!;
Ожидаемый результат:
- получен http-код: 401.
Статус: -
Приоритет: High


# TC-019

Название: Отправка запроса c передачей productId = null;
Шаги:
1. отправить GET запрос: /products/null/status?authToken=abcd123qwert5678;
Ожидаемый результат:
- получен http-код: 500.
- получен ответ в формате json {"errorMessage": ...}
Статус: -
Приоритет: High


# TC-020

Название: Отправка запроса c передачей recalculate=true, owner=Создатель, region=Северо-Запад;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=true&owner=Создатель&region=Северо-Запад;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в формате json {"productStatus": 0 или 1}
Статус: -
Приоритет: Medium


# TC-021

Название: Отправка запроса c передачей recalculate=true, owner=Пользователь, region=Сибирь;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=true&owner=Пользователь&region=Сибирь;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в формате json {"productStatus": 0 или 1}
Статус: -
Приоритет: Medium


# TC-022

Название: Отправка запроса c передачей recalculate=false, owner=Создатель, region=Поволжье;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=false&owner=Создатель&region=Поволжье;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в формате json {"productStatus": 0 или 1}
Статус: -
Приоритет: Medium


# TC-023

Название: Отправка запроса c передачей recalculate=false, owner=Пользователь, region=Северо-Запад;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&recalculate=false&owner=Пользователь&region=Северо-Запад;
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в формате json {"productStatus": 0 или 1}
Статус: -
Приоритет: Medium


# TC-024

Название: Отправка запроса c указанием region = null;
Шаги:
1. отправить GET запрос: /products/12/status?authToken=abcd123qwert5678&region=123;
Ожидаемый результат:
- получен http-код: 200 или 500;
- получен ответ в формате json {"productStatus": 0 или 1} или {"errorMessage": ...}
Статус: -
Приоритет: High