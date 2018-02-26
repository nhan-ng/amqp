# Connection

Connection добавляет к amqp.Connection контроль переподключения с сопутствующими параметрами.

## Параметры
#### WithLogger
Добавляет [go-kit-style](https://gokit.io) логгер.
Логгер сообщает об:
  * Отключении и подключении соединения.
  * Закрытии соединения.
  * Ошибки соединения.
  * Превышение максимального числа попыток.
  * Отмены соединения.

#### Attempts
Устанавливает максимальное количество попыток подключения. После успешного подключения, счетчик попыток сбрасывается.
По-умолчанию количество попыток не ограничено.

#### WithCancel
Устанавливает канал который будет слушать сигнал отмены механизма переподключения.
Не имеет эффекта, если соединение уже установлено. Для закрытия соединения используйте `Connection.Close()`.

#### WithDelay
Устанавливает задержку между попытками подключения. Задержка увеличивается после каждой попытки в 2 раза пока не достигнет значения `max`.
Первая задержка равна `min`.

#### WithDelayBuilder
Позволяет установить собственное правило ожидания. По-умолчанию используется правило, которое описано в WithDelay.

