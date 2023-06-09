# MWGPT - Новая нейросеть от MPMWORLD!

# Что это такое?
 
MWGPT - новая нейросеть, которая ищет ваш запрос в базе данных и отвечает на него. Вы можете добавлять ответы в базу.

# Инструкция по установке

В данной статье будет рассказано про получение и запись ответа с помощью Python.


Подготовка (для всего одинаковая):

Нам нужно получить токен для использования API. Переходим в дискорд сервер https://discord.gg/FzWP7GqcBg (выберите что вам нужно CatGPT SUPPORT), открываем любой канал где вы можете писать и пишем: ```/key```, выбираем бота с аватаркой кота и отправляем сообщение. ![image](https://github.com/win-compm/mwgpt/assets/79410241/c37d1523-f754-4a74-a84b-3a8dc5c72728) Наш ключ создан, нажимаем на сплойлер и копируем его. 


Установка:

Для начала нужно установить и импортировать модуль requests:
Прописываем в консоли: ```pip install requests```
Открываем файл бота и добавляем этот модуль для импортирования: ```import requests```

Теперь импортируем модуль json, его устанавливать не нужно: ```import json```


Получение ответа от API:

Дальше только код, ничего другого. Учтите, что это только фрагмент получения ответа, вам нужно ещё создать класс команды и отправить ответ (это вы сделайте уже без меня), так-же необходимо заменить переменные на ваше значение.
```
new = ваша_переменная_с_вопросом.replace('?', '') # убираем ? для правильной работы API 
resp = requests.get(f'http://gpt.api.nashka.ml:6191/gpt/{new}/auth/ваш_ключ') # Отправляем запрос
resp1 = json.loads(resp.text) # импортируем то, что мы получили как json
if resp1["status"] == "false": # проверка, если API выдал ошибку
    if resp1["error"] == "No answer": # проверка, если ошибка заключается в том, что ответ не найден
        # здесь вы должны сделать вывод ошибки "По запросу ничего не найдено, вы можете добавить ответ на этот вопрос."
    if resp1["error"] == "Key error": # проверка, если ошибка заключается в том, что в запросе не верный ключ (для устранение ошибки сгенерируйте ключ заного и замените его в переменной resp)
        # вывод технической ошибки неверного ключа
else: # если всё ок
    # вам нужно отправить ответ пользователю, ответ находится в переменной resp1["response"]
```

Хорошо, мы поняли как получить ответ, но как же его записать? Всё почти так-же!

```
new = ваша_переменная_с_вопросом.replace('?', '') # убираем ? для правильной работы API 
new2 = ваша_переменная_с_ответом_на_вопрос.replace('?', '') # убираем ? для правильной работы API 
resp = requests.get(f'http://gpt.api.nashka.ml:6191/addgpt/{new}/{new2}/auth/ваш_ключ') # Отправляем запрос
resp1 = json.loads(resp.text) # импортируем то, что мы получили как json
if resp1["status"] == "false": # проверка, если API выдал ошибку
    if resp1["error"] == "Already exists": # проверка, если ошибка заключается в том, что ответ на вопрос есть
        # здесь вы должны сделать вывод ошибки "Ответ на этот вопрос уже существует"
    if resp1["error"] == "Key error": # проверка, если ошибка заключается в том, что в запросе не верный ключ (для устранение ошибки сгенерируйте ключ заного и замените его в переменной resp)
        # вывод технической ошибки неверного ключа
else: # если всё ок
    # вам нужно отправить ответ пользователю, что ответ записан.
```


## Вот и всё! Приятного использовая MWGPT API! Ваш MPMWORLD 💖
