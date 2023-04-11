## Ошибка при запуске приложения Flaskex
Текст ошибки говорит о том, что не существует определённого атрибута ```required()``` у модуля `validators`.
 <br/>Есть два возможных решения:
 <br/>в строке `validators=[validators.required(), validators.Length(min=1, max=30)]`
1. Удалить `validators.required()`
2. Заменить `required()` на используемую в текущей версии библиотеки другой атрибут `DataRequired()`, 
   вид строки станет `validators=[validators.DataRequired(), validators.Length(min=1, max=30)]`

Эти же шаги касаются и строки с переменной `password`

## Создание и запуск образа Docker
+ `docker build -t flaskex .`
+ `docker run -p 5000:5000 flaskex`

Логи выполненной команды
```
$ docker run -p 5000:5000 flaskex
 * Serving Flask app 'app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://172.17.0.2:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 106-728-067
```

## Запуск образа с помощью Docker Compose
Созданный с помощью Docker Compose образ запускается без дополнительных команд запуска образа. 

+ `docker compose up`

Логи выполненной команды
```
$ docker compose up
[+] Running 2/0
 ✔ Container test-flaskex-redis-1  Created                                                                                                                                                                                              0.0s 
 ✔ Container test-flaskex-web-1    Created                                                                                                                                                                                              0.0s 
Attaching to test-flaskex-redis-1, test-flaskex-web-1
test-flaskex-redis-1  |  * Serving Flask app 'app'
test-flaskex-redis-1  |  * Debug mode: on
test-flaskex-redis-1  | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
test-flaskex-redis-1  |  * Running on all addresses (0.0.0.0)
test-flaskex-redis-1  |  * Running on http://127.0.0.1:5000
test-flaskex-redis-1  |  * Running on http://172.18.0.2:5000
test-flaskex-redis-1  | Press CTRL+C to quit
test-flaskex-redis-1  |  * Restarting with stat
test-flaskex-web-1    |  * Serving Flask app 'app'
test-flaskex-web-1    |  * Debug mode: on
test-flaskex-web-1    | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
test-flaskex-web-1    |  * Running on all addresses (0.0.0.0)
test-flaskex-web-1    |  * Running on http://127.0.0.1:5000
test-flaskex-web-1    |  * Running on http://172.18.0.3:5000
test-flaskex-web-1    | Press CTRL+C to quit
test-flaskex-web-1    |  * Restarting with stat
test-flaskex-redis-1  |  * Debugger is active!
test-flaskex-redis-1  |  * Debugger PIN: 122-943-564
test-flaskex-web-1    |  * Debugger is active!
test-flaskex-web-1    |  * Debugger PIN: 143-841-829
Gracefully stopping... (press Ctrl+C again to force)
Aborting on container exit...
[+] Running 0/2
 - Container test-flaskex-redis-1  Stopping                                                                                                                                                                                             0.2s 
 - Container test-flaskex-web-1    Stopping                                                                                                                                                                                             0.2s 
[+] Running 2/2
 ✔ Container test-flaskex-redis-1  Stopped                                                                                                                                                                                              0.4s 
 ✔ Container test-flaskex-web-1    Stopped                                                                                                                                                                                              0.6s 
canceled
```