---
title: Управление версиями. Git.
subtitle: В этом посте рассмотрим, что такое Управление версиями, а так же расскажу о Git.

# Summary for listings and search engines
summary: В этом посте рассмотрим, что такое Управление версиями, а так же расскажу о Git.

# Link this post with a project
projects: []

date: '2023-03-04'

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: true

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ''
  placement: 2
  preview_only: false

authors:
  - admin
  
tags:
  - Academic

categories:
  - Git
---

## Что такое Git

Git — это специальная программа, которая позволяет отслеживать любые изменения в файлах, хранить их версии и оперативно возвращаться в любое сохранённое состояние.

Большинство других систем контроля версий хранят информацию в виде списка изменений в файлах. Git работает иначе — он хранит скорее набор снимков — полное отображение того, как выглядит файл в момент сохранения. Это позволяет всегда иметь полную информацию обо всех файлах и быстро восстанавливать любую из предыдущих версий.

Рассмотрим, как это работает, на примере.

Есть проект, в котором пишется код. В нём создано окружение Git ― все изменения файлов отслеживаются в рамках настроенных параметров и заданных фильтров. Нужно добавить в проект новую функцию, изменив или доработав существующий код. Для этого потребуется создать внутри проекта отдельную ветку — в Git они называются branch. Работа в этой ветке никак не затрагивает основной код — если с новыми изменениями что-то пойдёт не так и код станет невалидным и перестанет запускаться, основной проект не пострадает. А когда новая функция будет дописана и протестирована, ветку можно будет «наложить» на основной код.

Также в рамках Git можно объединять разные версии кода в один. Например, над проектом трудится несколько программистов, и каждый разрабатывает или изменяет код в собственных ветках. В конце работы появится необходимость слить ветки вместе — и получается цельная программа. Это значительно облегчает совместную работу, так как не нужно ждать, пока другой разработчик допишет код, — можно работать параллельно.

Если же в одной из веток разработка пойдёт не по плану и произойдёт ошибка — всё можно просто откатить до предыдущей ветки в системе контроля версий Git, где ошибок не было. И начать разработку заново.

![Визуально ветки можно представить так](bran.jpg)

## Git может быть локальным, централизованным или распределённым:

● **Локальный** установлен на одном компьютере и хранит файлы только в одном экземпляре в рамках настроенного окружения — подходит, если программист пишет код в одиночку.

● **Централизованный** находится на общем севере и хранит все файлы на нем.

● **Распределённый хранит** данные и в общем облачном хранилище, и в устройствах участников команды.

Распределённая система лучше всего подходит для командной работы. Даже если с центральным хранилищем что-то случится, проект можно восстановить из копий участников команды.

Удобство и гибкость сделали Git стандартом для большинства современных IT-компаний. Поэтому умение работать с ним критично для любого программиста. 

## Принципы работы с Git

При работе с Git в среде разработчиков принято руководствоваться тремя принципами:

1. Регулярно коммитить ― сохранять изменения в Git. Такой подход позволит сохранять более подробную историю версий и быстро замечать ошибки в коде.
2. Создавать новые ветки. Они позволяют легко управлять изменениями, особенно параллельными. Лучше создать ещё одну ветку, чем что-то испортить в старой.
3. Чётко и лаконично описывать коммиты. Изменения кода, которые отправляются в Git, обязательно должны содержать пояснения и комментарии по добавленным правкам, доработкам и изменениям. Это значительно облегчает совместную работу и помогает быстрее разбираться в своем старом коде.

## Начало работы с Git: установка и настройка

Установить систему контроля версий Git можно по алгоритму:

1.	Перейти на страницу загрузки Git.
2.	Скачать дистрибутив для нужной операционной системы.
3.	Запустить установочный файл и следовать инструкциям на экране.
4.	После завершения установки открыть терминал или командную строку и ввести команду git --version. Если Git правильно установлен, отобразится версия Git.

Это схема для установки Git локально. Для серверов алгоритм в целом такой же, но потребуется ещё настроить взаимодействие с локальными устройствами — но это уже работа системного администратора.

Также для работы потребуется создать репозиторий в Git. Это можно сделать по схеме:

1.	Создать пустую директорию на диске.
2.	Перейти в созданную папку и запустить терминал.
3.	Инициализировать репозиторий командой git init. После выполнения этой команды в директории появится скрытая папка .git
4.	Добавить в репозиторий файлы командой git add. После указанной команды выбранные файлы перейдут в статус «отслеживаемых» и можно будет увидеть производимые с ними изменения ― удаление, перемещение, переименование и изменения содержимого файлов.
5.	Создать первый коммит командой git commit -m "Initial commit".
6.	Создать ветку в Git командой git branch <название_ветки>

Чтобы полностью понять, как использовать Git, нужно изучить все его основные команды. Это можно сделать в документации.

«Джентльменским набором» для работы в Git можно считать набор команд:

●	git commit — фиксация изменений

●	git diff — просмотр актуальных или предыдущих изменений в рамках работы над репозиторием

●	git checkout — переход на предыдущее состояние или ветку

●	git push/pull — отправка и получение изменений из удалённого репозитория

●	git stash — сохранение изменений в архив для последующего использования


## Что такое репозиторий Git

Репозиторий — это место, в котором хранится весь код и вся история его изменений. По сути это просто папка, однако она связана с Git напрямую и содержит файлы в понятном для Git формате. Кроме того, для папки, заявленной как репозиторий, Git формирует историю изменений.

Репозиторий может быть локальным ― храниться на компьютере пользователя. А может быть удалённым — лежать на сервере или в облачном хранилище. В таком случае пользователи со своих устройств подключаются к этому репозиторию через интернет.

![Интерфейс GitHub](ui.jpg)