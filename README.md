Описание формата API системы Партнёр.Онлайн
# О сервисе
Партнёр.Онлайн – это SaaS-сервис для автоматического заполнения реквизитов контрагентов на основе сведений из ЕГРЮЛ.
# Общие сведения
  - Базовый URL для методов API расположен по адресу https://partner.vladelets.online
  - Обмен данными с сервисом  осуществляется по протоколу HTTPS.
  - Формат данных ответа – JSON.
  - Параметры в запроса должны быть в кодировке UTF-8 и закодированы для передачи в URL (http://en.wikipedia.org/wiki/Percent-encoding).
# Аутентификация
Для доступа к методам сервиса требуется HTTP Basic over HTTPS аутентификация. Для получения токена обратитесь на почту sales@vladelets.online.

# Методы
В этом разделе описаны возможные запросы к API и форматы ответа на них.
### Поиск организаций
#### Запрос
`GET /api/v1/company`
#### Параметры
| Параметр | Тип | Описание |
| ------ | ------ | ------ |
| inn | строка 10 цифр, необязательный | ИНН организации |
| ogrn | строка из 13 цифр, необязательный | ОГРН организации |
| name | строка, необязательный | Наименование организации 

В запросе должен быть передан по крайней мере один из этих параметров. В случае передачи двух и более параметров поиск будет производиться по соответствию всех переданных значений (логическое "И").
#### Формат ответа
```json
{"results" : [
    {
        "full_name":"ЕАЕ",
        "compact_name":"ООО \"ЕАЕ\"",
        "inn":7734517839,
        "kpp":773401001,
        "ogrn":1047796788930,
        "address":"г. Москва, ул. Демьяна Бедного, владение 24",
        "region":{  
           "description":"г. Москва",
           "full_name":"Москва",
           "full_type":"город",
           "short_type":"г.",
           "short_name":"",
           "display_type":1,
           "code":"77"
         },
        "form":{  
           "compact_form":"ООО",
           "full_form":"Общество с ограниченной ответственностью",
           "code":"12300"
        },
        "head":{  
           "position":"Руководитель",
           "inn":"771811057155",
           "first_name":"Владимир",
           "last_name":"Иванов",
           "middle_name":"Иванович",
        }
    }      
]}
```
По вопросам работы с API обращайтесь на support@vladelets.online
