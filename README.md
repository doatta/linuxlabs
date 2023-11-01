# О лабораторных

Этот репозиторий позволяет собрать лабораторную для обучения и практики. Сами лабораторные выполнены в виде [jupyter документов](https://jupyter.org/), в которых можно совмещать чтение и запуск команд/скриптов.

Блоки с кодом выделены таким образом:

```
[] systemctl status httpd
```

Вы читаете текст, нажимаете мышкой на области с кодом и нажимаете Shift+Enter. Во время выполнения чекбокс рядом с блоком кода меняется на `[*]`. А после выполнения в нём появляется порядковый номер выполнения `[1]`. Пример можно пощупать на [официальном сайте](https://jupyter.org/try-jupyter/lab/).

Список готовых лабораторных можно увидеть в директории `labs/jupyter/tasks`.

# Пререквизиты

Для доступа к лабораторным вам нужно система с:

- docker
- docker-compose
- браузер

# Вкратце

Поднимаете контейнеры с `docker-compose.yaml`, в одном из контейнеров - `labs-jupyter` - размещен jupyter, ссылку для доступа к которому можно найти в логах контейнера. В браузере открываете ссылку - и там в левой панели будут доступны лабораторные - файлы с расширением ipynb.

# Установка на Linux

1. Собираем контейнеры:

```
docker-compose up -d
```

2. Смотрим логи контейнера с `jupyter` и ищем строку с `http://127.0.0.1:8888/lab?token=`:

```
docker-compose logs jupyter | grep http://127.0.0.1:8888/
```

3. Копируем ссылку и вставляем в браузере.

