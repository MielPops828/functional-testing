Bug-Report-001. Создание существующей папки

Тип: Bug;
Серьёзность: Trivial;
Приоритет: Low;
Предусловия:
- Сформирован валидный OAuth токен;
- На диске существует папка "test"
    - Скриншот содержимых файлов на диске:
    ![alt text](image-5.png)
Шаги:
1. Отправить PUT запрос: https://cloud-api.yandex.net/v1/disk/resources?path=test;
Ожидаемый результат:
- Получен http-код: 401;
- Получено тело ответа json формата { "message": "string", "description": "string", "error": "string" };
- Папка не была создана.
Фактический результат:
- Получен http-код: 409 (Conflict);
- Получено тело ответа json формата { "error": "string", "description": "string", "message": "string" };
- Папка не была создана.
Скриншот фактического результата:
![alt text](image-3.png)