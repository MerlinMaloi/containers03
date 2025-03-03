
# Первый контейнер

## Цель работы:

Лабораторная работа чтобы ознакомиться с основами контейнеризации и подготовить рабочее место для выполнения следующих лабораторных работ.

## Задание

Установить Docker Desktop и проверить его работоспособность.

## Описание выполнения работы с ответами на вопросы

1. Скачал и установил Docker Desktop. В процессе  установки столкнулся с проблемами нехватки памяти на диске C , пытался установить на диск D, не получилось в связи с неудачным перемещением папок. Вернулся к варианту установки на диск C для этого освободил память , а также в терминале обновил WSL так как Docker не может подключиться к своему движку (Docker Desktop Linux Engine)

2. Потом создал на GH(GitHub) репозиторий containers03 и клонировал его на диск F своего компьютера. В нем создал файлы Dockerfile , README.md .  В Dockerfile добавил следующее содержимое:

''' 
FROM debian:latest
COPY ./site/ /var/www/html/
CMD ["sh", "-c", "echo hello from $HOSTNAME"] 
'''

В containers03 создал папку site,  в новой папке создал файл index.html с произвольным содержимым.

3. В VS Code открыл папку containers03 и терминал. Там использовал команды ' docker -v ' чтобы убедиться в работоспособности докера , далее ' docker build -t containers02 . ' 

*Сколько времени создавался образ?*

Образ создавался 42 секунды : ' Building 42.2s '

Далее выполнил команду для запуска контейнера: ' docker run --name containers03 containers03 '

*Что было выведено в консоли?*

Было выведено: ' hello from 7f1a76d84309 '

Удалил контейнер и снова запустил, выполнив команды:

'''
docker rm containers03
docker run -ti --name containers03 containers03 bash
'''

В открывшемся окне выполнил команды:

'''
cd /var/www/html/ 
ls -l
'''

*Что выводится на экране?*

'''
root@486bd9603873:/# cd /var/www/html/
root@486bd9603873:/var/www/html# ls -l
total 4
-rwxr-xr-x 1 root root 291 Mar  2 21:42 index.html
'''

4. Закрыл окно командой  ' exit ' 

## Выводы

В ходе выполнения работы я ознакомился с прорблематичной установкой Dockerа и попробовал создать образ в котором запустил контейнер. Тем самым получил начальные знания о работе с контейнирами, которые в дальнейшем понадобятся для следующих лабораторных работ

## Используемые источники

https://chatgpt.com/

Курс moodle usm : "Контейнеризация и виртуализация"
