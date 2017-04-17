Описание формата API системы Владелец.Онлайн
# О сервисе
Владелец.Онлайн – это SaaS-сервис для автоматического заполнения реквизитов контрагентов на основе сведений из ЕГРЮЛ.
# Общие сведения
  - Базовый URL для методов API расположен по адресу https://api.vladelets.online
  - Обмен данными с сервисом  осуществляется по протоколу HTTPS.
  - Формат данных ответа – JSON.
  - Параметры в запроса должны быть в кодировке UTF-8 и закодированы для передачи в URL (http://en.wikipedia.org/wiki/Percent-encoding).
# Аутентификация
Для доступа к методам сервиса требуется передавать аутентификационный JWT-токен в заголовке Authorization с использованием схемы Bearer. Срок действия токена – 365 дней.
Для получения токена обратитесь на почту sales@vladelets.online.

# Методы
В этом разделе описаны возможные запросы к API и форматы ответа на них.
### Поиск организаций
#### Запрос
`GET /v1/companies`
#### Параметры
| Параметр | Тип | Формат | Описание |
| ------ | ------ | ------ | ------ |
| inn | GET | строка 10 цифр, необязательный | ИНН организации |
| kpp | GET | строка 9 цифр, необязательный | КПП организации |
| ogrn | GET | строка из 13 цифр, необязательный | ОГРН организации |
| name | GET | строка, необязательный | Наименование организации 

В запросе должен быть передан по крайней мере один из этих параметров. В случае передачи двух и более параметров поиск будет производиться по соответствию всех переданных значений (логическое "И").
#### Пример запроса
`https://api.vladelets.online/api/v1/?inn=7734517839&kpp=773401001`
#### Пример ответа
```json
{
   "results":[
      {
         "full_name":"ЕАЕ",
         "compact_name":"ООО \"ЕАЕ\"",
         "inn":7734517839,
         "kpp":773401001,
         "ogrn":1047796788930,
         "okpo":75577697,
         "okato":77401367000,
         "registration_date":"2004-10-19",
         "tax_inspection_code":"5906",
         "is_bank":false,
         "address":{
            "full":"123308, г. Москва, ул. Демьяна Бедного, владение 24, к. 2а, строение III, кв. 3",
            "postal_code":"123308",
            "country":"Российская Федерация",
            "federal_district":"Центральный",
            "region":{
               "full":"Пермский край",
               "code":"77",
               "name":"Пермский",
               "type":"край"
            },
            "city":{
               "full":"г. Пермь",
               "name":"Пермь",
               "type":"город"
            },
            "street":"ул. Демьяна Бедного",
            "house":"владение 24",
            "housing":"к. 2а, строение III",
            "room":"кв. 3"
         },
         "form":{
            "compact_form":"ООО",
            "full_form":"Общество с ограниченной ответственностью",
            "code":"12300"
         },
         "head":{
            "position":"Руководитель",
            "inn":"771811057155",
            "last_name":"Иванов",
            "first_name":"Владимир",
            "middle_name":"Иванович"
         },
         "okved":[
            {
               "code":"63.11.1",
               "description":"Деятельность по созданию и использованию баз данных и информационных ресурсов",
               "is_primary":true
            },
            {
               "code":"68.32",
               "description":"Управление недвижимым имуществом за вознаграждение или на договорной основе"
            },
            {
               "code":"95.11",
               "description":"Ремонт компьютеров и периферийного компьютерного оборудования"
            }
         ]
      }
   ]
}
```
По вопросам работы с API обращайтесь на support@vladelets.online
