# Практика 2. Основы работы с библиотекой OpenCV

[![Build Status](https://travis-ci.org/Itseez-NNSU-SummerSchool2015/practice2-opencv-intro.svg)](https://travis-ci.org/Itseez-NNSU-SummerSchool2015/practice2-opencv-intro)

## Цели

__Цель данной работы__ - изучить базовые примитивы модуля `opencv_core`
и простейшие операции обработки изображений модуля `opencv_imgproc`, научиться
разрабатывать интерфейс средствами модуля `opencv_highgui`.

Проект представляет собой шаблон проекта для освоения основ работы
с библиотекой OpenCV:

  - Базовые примитивы и операции модуля `opencv_core`
    (методы класса `cv::Mat` для представления изображения).
  - Обработка изображений с помощью простеших фильтров модуля `opencv_imgproc`
    (линейные фильтры, вычисление градиентов на изображении).
  - Основные операции модуля `opencv_highgui` (загрузка	изображения 
    средствами `imread`, сохранение изображения с использованием
    `imwrite`, отображение изображения с помощью функций `imshow` и `waitKey`,
    реализация сложных сценариев обработки событий).

## Общая структура проекта

Структура проекта:

  - `sample_template` - исходные коды шаблонного проекта. Шаблонное
    приложение отображает исходное изображение и изображение, полученное
    в результате медианной фильтрации центральной части исходного изображения.
    Также в окне имеется 2 кнопки, позволяющие включить/отключить действие
    фильтра.
  - `testdata` - директория с данными для тестов.
  - `.gitignore` - перечень расширений файлов, которые не выкладываются
    в проект.
  - `.travis.yml` - конфигурационный файл для системы автоматического
    тестирования Travis-CI.
  - `CMakeLists.txt` - общий файл для сборки проекта с помощью CMake.
  - `README.md` - информация о проекте, которую вы сейчас читаете.

В шаблонном проекте имеются следующие модули:

  - Основной модуль `main`, содержащий реализацию основного сценария работы
    шаблонного приложения: разбор аргументов командной строки, чтение кадра,
    ожидание нажатия на кнопки и обновление состояния окна с изображениями.
  - Модуль `processing` содержит метод медианной фильтрации центральной области
    изображения.
  - Модуль графичекого приложения `application`. Содержит метод обработки
    аргументов командной строки `parseArguments`; обертку `processFrame` 
    над функцией обработки изображения с использованием метода, 
    реализованного в модуле	`processing`; метод отображения окна с двуми
    изображениями - исходным и обработанным, если фильтр включен, либо двумя
    исходными, если фильтр выключен; методы, необходимые для обработки событий
    нажатия на кнопки включение/выключения фильтра.

## Задачи

__Основные задачи:__

  1. Обеспечить возможность изменения положения региона фильтрации со временем.
  2. Добавить третью кнопку, чтобы обеспечить возможность сохранения текущего
     изображения окна (пара изображений).
  3. Добавить несколько дополнительных кнопок, позволяющих изменять тип фильтра:
     - Перевод центральной части изображения в оттенки серого вместо медианной
       фильтрации.
     - Поддержка режима пикселизации центральной области изображения (подобно
       тому, как на телевидении скрывают лицо человека).
     - Применение Канни детектора для определения ребер в центральной части
       исходного изображения.
  4. Реализовать возможность получения кадров из видеофайла и/или камеры.

__Дополнительные задачи:__
  
  1. Реализовать случайное перемешивание картинки как в игре в "пятнашки".
  2. Реализовать приложение для игры в пятнашки.
  
## Общая последовательность действий

  1. Сделать форк upstream-репозитория (раздел 
     [Общие инструкции по работе с Git](https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools#Общие-инструкции-по-работе-с-git)
     в [практической работе по освоению инструментов разработки ПО](https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools)).
  2. Клонировать origin к себе на локальную машину (раздел 
     [Общие инструкции по работе с Git](https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools#Общие-инструкции-по-работе-с-git)
     в [практической работе по освоению инструментов разработки ПО](https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools)).
  3. Скомпилировать и запустить сэмпл на картинке (раздел 
     [Сборка проекта с помощью CMake и MS VS](https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools#Сборка-проекта-с-помощью-cmake-и-microsoft-visual-studio)
     в [практической работе по освоению инструментов разработки ПО](https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools)).
  4. Создать копию директории с сэмплом, добавить ее построение в общий
     `CMakeLists.txt`.
  5. Убедиться, что новый сэмпл успешно собирается и запускается. 
  6. Прислать Pull Request с еще неизмененным сэмплом. Пометить в конце
     названия `(NOT READY)`. По мере готовности решений основных задач Pull
     Request можно будет переименовать.
  7. Сделать так, чтобы регион фильтрации менял со временем свое положение и
     размеры. Прислать Rull Request.
  4. Добавить третью кнопку, позволяющую сохранить текущее изображение на
     экране. Сохранять можно в текущую директорию с меткой времени. Прислать
     pull request.
  5. Добавить несколько дополнительных кнопок, позволяющих менять тип фильтра
    (см. перечень ниже) и прислать Rull Request.
     - Простой перевод в оттенки серого (функция 
       [cvtColor](http://docs.opencv.org/modules/imgproc/doc/miscellaneous_transformations.html#cvtcolor)).
     - Режим пикселизации (подробнее можно прочитать 
       [здесь](http://opencv-code.com/tutorials/photo-to-colored-dot-patterns-with-opencv)).
     - Режим применения Канни детектора (пример использования функции
       [Canny](http://docs.opencv.org/doc/tutorials/imgproc/imgtrans/canny_detector/canny_detector.html)).
  6. Реализовать возможность получения кадров с камеры и видеофайлов. Добавить
     соответствующие аргументы командной строки. Прислать Rull Request.
  7. Решить задачи из списка
     [Дополнительные задачи](https://github.com/Itseez-NNSU-SummerSchool2015/practice2-opencv-intro#Задачи).

## Детальная инструкция по выполнению работы

  1. Создать аккаунт на [github.com](https://github.com), если такой
     отсутствует. Для определенности обозначим аккаунт `github-account`.

  2. Сделать fork репозитория
     <https://github.com/Itseez-NNSU-SummerSchool2015/practice2-opencv-intro>
     (в терминологии Git upstream-репозиторий) к себе в организацию с названием
     `github-account`. В результате будет создана копию репозитория с названием
     <https://github.com/github-account/practice2-opencv-intro>
     (origin-репозиторий).

  3. Клонировать репозиторий [origin][origin] к себе на локальный компьютер,
     воспользовавшись следующей командой:

  ```
  $ git clone https://github.com/github-account/practice2-opencv-intro
  ```

  4. Настроить upstream-репозиторий:

  ```
  $ git remote add upstream https://github.com/Itseez-NNSU-SummerSchool2015/practice2-opencv-intro
  ```

  5. Настроить имя пользователя, из под которого будут выполняться
     все операции с репозиторией Git:

  ```
  $ git config --global user.name "github-account"
  ```

  6. Создать ветку `find-contours-implementation` и перейти в нее:

  ```
  $ git checkout -b find-contours-implementation
  ```

  7. В ветку `find-contours-implementation` поместить реализации различных
     методов поиска контуров, снабдив весь разработанный код необходимым
     набором тестов. В качестве шаблона необходимо использовать модуль
     `img_proc`. Модуль должен быть расширен различными реализациями методов
     поиска контуров на изображении средствами OpenCV. Для начала имеет смысл
     сосредоточиться на реализации одного метода из перечисленных ниже.

     1. Бинаризация изображения (функция `threshold`) + поиск контуров
        (функция `findContours`). Примечание: для отображения контуров
        следует использовать функцию `drawContours`.
     2. Морфологический градиент (функция `morphologyEx`).
     3. Оператор Собеля (функция `Sobel`).
     4. Оператор Лапласа (функция `Laplacian`).
     5. Детектор ребер Канни (функция `Canny`). Примечание: перед применением
        фильтра Канни потребуется выполнить фильтрацию и преобразование
        изображения в оттенки серого.

  8. Создать ветку `gui-implementation` и перейти в нее:

  ```
  $ git checkout -b gui-implementation
  ```

  9. В ветку `gui-implementation` поместить разработанную интерфейсную часть.
     Примечание: по существу необходимо разработать пример использования
     реализованного метода поиска контуров. Далее приведены возможные
     варианты реализации интерфейса в порядке их усложнения с точки зрения
     программной реализации.

     1. Отобразите одновременно в одном окне исходное изображение и изображение
        с выделенными контурами.

        *Указание:* воспользуйтесь имеющимся примером отображения результата
        медианной фильтрации.

     2. Добавьте внизу окна виртуальные кнопки (на самом деле одноцветные
        изображения), каждая из которых соответствует вызову определенного
        метода выделения контуров изображении. Не забудьте на них добавить
        соответствующие надписи. Обеспечьте возможность обновления результата
        выделения контуров при нажатии на каждую из кнопок.

        *Указание:* следует использовать возможность создания обработчика
        события нажатия на кнопку, отслеживая положение курсора в каждый
        текущий момент времени, чтобы определить, какой метод поиска контуров
        необходимо вызвать.

     __Примечание:__ примеров использования библиотеки может быть в проекте
     много. Когда разработан какой-то метод стоит его снабдить простым примером
     использования. Если задача выделения контуров решена уже несколькими
     способами, то можно подумать над усложненными вариантом интерфейса, который
     объединяет возможности использования различных способов выделения контуров.

  10. После получения каждой стабильной версии не забывайте проверять
      работоспособность тестов и выкладывать изменения в ветку.

  ```
  $ git status # Получить список текущих изменений

  $ git add [<file_name>] # Добавить файл в репозиторий
  # <file_name> - название файла для добавления в commit
    если вместо имени указан символ *, то будут добавлены все новые файлы,
    расширение которых не указано в .gitignore

  $ git commit [-m "<message_to_commit>"] [-a]
  # [-a] - автоматически добавляет изменения для существующих на сервере файлов
    без выполнения команды git add
  # [--amend] - перезаписывает последний коммит (используется, если не забыты
    изменения)

  $ git push origin find-contours-implementation # или gui-implementation
  ```

  11. Не забудьте сделать Pull Request, чтобы проверить работоспособность
      тестов на Travis-CI и позволить преподавателям сделать ревью Вашего кода.

  __Примечание:__ подробная инструкция по сборке проекта, запуску тестов была
  описана в [практической работе по освоению инструментов разработки]
  (https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools). При
  сборке проекта в командной строке `cmake` необходимо указать опцию
  `-DOpenCV_DIR="path-to-OpenCVConfig.cmake"`, чтобы подключить библиотеку
  OpenCV.

  12. При наличии времени можно организовать обработку видео и вместо одного
      изображения обрабатывать и отображать последовательно идущие кадры
      потока.

<!-- LINKS -->

[origin]: https://github.com/github-account/practice2-opencv-intro
