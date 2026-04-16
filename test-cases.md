# TC-001

Название: Проверка успешного получения статуса продукта;
Предусловия:
- productId существует;
- есть authToken из 16 символов.
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = abcd123qwert5678);
Ожидаемый результат:
- получен http-код: 200;
- получен ответ в json формате: { "productStatus": 0 или 1 }.
Фактический результат: -
Статус: -
Приоритет: High

# TC-002

Название: Отправка запроса без authToken;
Предусловия:
- валидный productId существует;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = null);
Ожидаемый результат:
- получен http-код: 401.
Фактический результат: -
Статус: -
Приоритет: High

# TC-003

Название: Отправка запроса c указанием несуществующего productId;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = prod123, authToken = abcd123qwert5678);
Ожидаемый результат:
- получен http-код: 404.
Фактический результат: -
Статус: -
Приоритет: High

# TC-004

Название: Отправка запроса c указанием невалидного токена;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = qwerty123);
Ожидаемый результат:
- получен http-код: 401.
Фактический результат: -
Статус: -
Приоритет: High

# TC-005

Название: Отправка запроса c указанием recalculate=true;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = abcd123qwert5678, recalculate = true);
Ожидаемый результат:
- получен http-код: 200;
- получен ответ в json формате: { "productStatus": 0 или 1}
Фактический результат: -
Статус: -
Приоритет: High

# TC-006

Название: Отправка запроса c указанием невалидного recalculate;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = qwerty123, recalculate = abc);
Ожидаемый результат:
- получен http-код: 400.
Фактический результат: -
Статус: -
Приоритет: High

# TC-007

Название: Отправка запроса c указанием невалидного owner;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = qwerty123, owner = 123);
Ожидаемый результат:
- получен http-код: 400.
Фактический результат: -
Статус: -
Приоритет: High

# TC-008

Название: Отправка запроса c указанием owner = Создатель;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = qwerty123, owner = Создатель);
Ожидаемый результат:
- получен http-код: 200;
- получен ответ в json формате: { "productStatus": 0 или 1}
Фактический результат: -
Статус: -
Приоритет: High

# TC-009

Название: Отправка запроса c указанием region = Северо-Запад;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = qwerty123, region = Сервер-Запад);
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в json формате: { "productStatus": 0 или 1}
Фактический результат: -
Статус: -
Приоритет: High

# TC-010

Название: Отправка запроса c указанием невалидного region;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = qwerty123, region = 123);
Ожидаемый результат:
- получен http-код: 400.
Фактический результат: -
Статус: -
Приоритет: High

# TC-011

Название: Отправка запроса c указанием всех параметров;
Шаги:
1. отправить GET запрос: /products/{productId}/status?authToken=&recalculate=&owner=&region= (productId = 12, authToken = abcd123qwert5678, recalculate = true, owner = Создатель, region = Северо-Запад);
Ожидаемый результат:
- получен http-код: 200.
- получен ответ в json формате: { "productStatus": 0 или 1}
Фактический результат: -
Статус: -
Приоритет: High