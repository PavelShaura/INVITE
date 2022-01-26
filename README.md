1. При запуске бота все таблицы базы данных обнуляются и создаются. В БД Админ заносится первый админ.
Только он сможет добавлять, удалять и т.д. администраторов.
2. Админы смогут добавлять и удалять и т.д. модераторов и пользователей.
3. Модераторы смогут добавлять и удалять и т.д. пользователей.
4. Из команд только /start у всех.
Команда /start будет в зависимости от роли пользователя открывать клавиатуру с возможными командами
5. При нажатии на старт у всех будет проверяться username 



ТЗ на разработку Telegram-бота онлайн-знакомств
=========================================


1 Описание

Система имеет три роли:
- пользователи;
- модераторы (проверяют пользователей, блокируют/разблокируют пользователей);
- администраторы.

Пользователи бота просматривают карточки с другими пользователями и ставят «Симпатию» либо «Пропуск». Если два 
пользователя поставили друг другу «Симпатию», то образуется «Пара». После образования пары пользователям доступны 
контакты друг друга (username в Telegram). 

Каждый пользователь должен пройти модерацию, модератор в своей панели управления видят всех пользователей, ожидающий 
проверки. Администратор видит вообще всех пользователей и может установить модерацию для каждого из них пройденной или 
непройденной.


2 Основной функционал

2.1 Пользователи

2.1.1 Создание профиля на сайте. 

При первом заходе в бот указываются следующие поля:
- имя;
- возраст;
- пол;
- биография (текст);
- от 1 до 10 фото;
- ищу м или ж;
- ищу возраст от и до;
- локация поиска;
- радиус поиска.

У пользователя для работы с ботом должен быть установлен username в Telegram, иначе регистрация не запускается, и 
выводится сообщение с соответствующим текстом. Все вышеперечисленные поля обязательны для заполнения и доступы позднее 
для изменения в настройках.

2.1.2 Просмотр карточек пользователей по заданным критериям поиска.
Используя заданные в настройках параметры поиска (ищу м или ж, ищу возраст от и до, локация и радиус) пользователи 
просматривают по одному человеку с помощью InlineKeyboard. После нажатия на «Симпатию» или «Пропуск» отменить данное 
действие нельзя. Также есть возможность отправить жалобу на карточку пользователя с указанием причины (из списка 
заданных администратором либо свою текстом).

2.1.3 Страница «Я нравлюсь им» со списком пользователей, которые поставили данному пользователю «Симпатию». 
Для каждого из этих профилей есть возможность оставить взаимную «Симпатию» (образуется «Пара») либо «Пропуск» 
(пользователь удаляется со странице «Я нравлюсь им»).

2.1.4 Страница «Мои пары» со списком профилей. Непросмотренные профили помечаются (условно звездочкой). При заходе в 
карточку пользователя, с которым образовалась «Пара», отображается информация пользователя + его username для связи 
(контакт). Поиск среди своих «Пар» по имени, фильтр по возрасту.

2.1.5 Страница «Мои настройки». Редактирование всей информации, указанной на этапе регистрации.

2.1.6 Страница «Люди рядом» с сортировкой пользователей по дистанции относительно локации, заданной текущим 
пользователем.

2.2 Модераторы

Модератор имеет весь функционал Пользователя включительно.

2.2.1 Страница  с пользователями, ожидающими прохождения модерации. Возможность подтвердить или отклонить модерацию.

2.2.1 Страница с пользователям, на которых жаловались. Возможность заблокировать аккаунт (временно или навсегда). 
В базе данных блокировка фиксируется за определенным модератором, чтобы было понятно, кто принял решение о блокировке.

2.3 Администраторы

Администратор имеет весь функционал Модератора включительно.

2.3.1 Страница со всеми пользователям (N записей на странице, задается в настройках). По каждому пользователю можно 
совершить следующие действия:
- блокировка (временная или постоянная) или разблокировка; В случае блокировки пользователю отправляется заданное сообщение;
- подтвердить или отклонить модерацию;
- изменить информацию, введенную пользователем при регистрации.
- отправить сообщение от имени бота.

2.3.2 Рассылка всем пользователям.


3 Техническая часть

3.1 Язык программирования: Python.

3.2 СУБД: PostgreSQL. Библиотека для работы с PostgreSQL из Python – Gino.

3.3 Библиотека разработки бота: aiogram.

3.4 У страниц с несколькими однородными объектами должна быть пагинация, задаваемая в настройках бота перед запуском.

3.5 Все настройки должны быть вынесены в конфигурационный файл или соответсвующие записи БД.

3.6 Логирование.
