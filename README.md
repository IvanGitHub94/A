# Battery report (Отчет об износе батареи)
v1.0

## --- ВНИМАНИЕ! ---
Программа предназначена для запуска на устройствах с аккумуляторной батареей и ОС Windows (рекомендуются версии после Windows 7).

## Краткое описание:

Программа показывает степень износа АКБ устройства в %.

## Принцип работы:

1. В Java-коде вызывается приложение "cmd.exe" с передачей команды "powercfg /batteryreport" (при этом выполняется переход на диск "C").
2. ОС генерирует файл (отчет о состоянии АКБ) в формате .html . Файл создается в том каталоге, из которого запускается программа.
3. Программа выполняет парсинг готового файла с помощью библиотеки jsoup (1.14.3).
4. Выполняется расчет с использованием данных парсинга. Используются показатели "DESIGN CAPACITY" и "FULL CHARGE CAPACITY" (Расчетная емкость и Последняя полная зарядка). 
5. Формула расчета: (DESIGN CAPACITY - FULL CHARGE CAPACITY) / DESIGN CAPACITY * 100.0
6. В окне отображается результат вычислений в процентах и путь к файлу (п. 2).

## Используемые технологии:
1. SDK 1.8 (Java 8)
2. JavaFX
3. jsoup (1.14.3)
4. Используемые библиотеки находятся в папке li

## Особенности установки и запуска:
1. Для запуска из intellij idea достаточно клонировать репозиторий, открыть его как новый проект в среде и запустить класс Main.
2. Для запуска jar-файла на целевом устройстве необходимо наличие установленной Java (JRE) от 8 версии.
3. В репозиторий https://github.com/IvanGitHub94/A1.git отдельно вынесена папка с файлами для запуска. Так же присутствует exe-файл с программой. Файл необходимо запускать из того же каталога, где находится папка "run". 
Упаковка jar в exe производилась при помощи ПО Launch4j с принудительным использованием поставляемой JRE для случаев, когда в ОС не предустановлена Java.
Это значительно увеличивает размер программы, но позволяет запускать ее без установки Java.
