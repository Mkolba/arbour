# Arbour
## Методы API:

- **ai.recognizeEmotions [POST-запрос]**
    - Распознает эмоции на .jpg фотографии человека, переданной в multipart/form-data. 
Возвращает преобладающую эмоцию в поле JSON объекта `data -> dominant_emotion`


## Взаимодействие с WebSocket сервером:
> Веб-сокеты позволяют моментально доставлять информацию от микроконтроллера к серверу и наоборот.

Для подключения к серверу вам нужно открыть соединение с адресом `wss://domain.ru/ws?token=ARDUINO_TOKEN`  
Передача данных осуществляется путем отправки JSON объектов типа `{"type": ТИП_СОБЫТИЯ, "field": ДАННЫЕ}`

- Поддерживаются следующие типы событий для передачи:
    - updateSensor - обновление показаний датчика для отображения в веб-интерфейсе.  
`{"type": "updateSensor", "sensor": "sensor_name", "new_value": float}`
    - securityAlert - оповещение о нарушении безопасности объекта. Отправит оповещение всем подписанным пользователям.  
`{"type": "securityAlert", "title": "Title", "description": "Any Text"}`

