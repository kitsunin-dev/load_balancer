## Реализация сетевого балансировщика нагрузки

#### Функционал балансировщика:
- Читает настройки из config.conf
- Принимает UDP-датаграммы от клиента
- Поочередно направляет датаграммы к серверам (узлам)
- Ограничивает кол-во переправляемых датаграмм в секунду

#### Строение папки:

1. Программы на языке C++
client.cpp - реализация клиентной части
balancer.cpp - реализация собственно сетевого балансировщика нагрузки
server1.cpp - реализация первого сервера*
server2.cpp - реализация второго сервера
server3.cpp - реализация третьего сервера
* все реализации серверов идентичны и отличаются лишь адресами (портами) в директиве #define PORT

2. config.conf - конфигурационный файл. Состоит из трех строк (которые можно изменять):
Первая строка - номер порта, с которого работает балансировщик
Вторая строка - адреса (порты) серверов через запятую
Третья строка - макс. кол-во датаграмм, обрабатываемых в секунду

3. shell-скрипты (*.sh) - используются для более удобной компиляции соответствующих файлов .cpp

4. example.mp4 - видео с компиляцией проекта и примером работы балансировщика

Для корректной работы системы нужно:
- открыть несколько терминалов (по одному терминалу на каждую программу)
- запустить shell-скрипт в каждом терминале (./*.sh, где * - имя соотв. файла cpp)
После этого действия в папке появятся объектный и исполняемый файлы
- запустить исполняемый файл (./*, где * - имя соотв. файла cpp)

Для завершения работы программы нужно нажать Ctrl+C в соотв. терминале.
