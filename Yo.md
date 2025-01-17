# Команда Yo
## https://bmstusa.ru

# Отчет по тестам

Тестовое окружение: 
Ubuntu 20.04, 8 гб ОЗУ, экран 15,6”, 1920х1080, браузер Chrome v95.0.4638.69

Тестируемые разделы:
1. Регистрация
2. Логин
3. Хедер
4. Страница профиля
5. Страница мероприятия
6. Страница Создание мероприятия
7. Страница Редактирование мероприятия
8. Главная страница

### Регистрация
https://bmstusa.ru/signup
- Поле ”Имя” и “Фамилия”:
    1. Есть ограничение на ввод некорректных символов. (Имена и фамилии должны содержать только буквы, но имена и фамилии с дефисом валидны)
    2. BUG: Буква ё не считается буквой в полях ввода, следовательно не проходит контроль.
    3. Нельзя вводить пустое поле.
- Поле “Email”:
    1. При вводе ранее зарегистрированной почты выводит сообщение, что пользователь уже зарегистрирован.
    2. Нельзя вводить пустое поле.
    3. Есть ограничение на ввод.
(поле email требует строку формата mail@mail.ru).
- Поля “Пароль” и “Повторить пароль”:
    1. Есть ограничение на ввод. Требуется не менее 8-ми символов.
    2. Нельзя вводить пустое поле.
    3. При несовпадении паролей выдаёт сообщение о несоответствии.
- Кнопка “Назад”:
	1. Возвращает на предыдущую страницу.
- Кнопка “Зарегистрироваться”:
	1. При корректном вводе переводит на страницу https://bmstusa.ru.
	2. При некорректом вводе подсвечиваются красным поля с ошибочными данными.


### Логин
https://bmstusa.ru/login
- Поле “Email”:
    1. Нельзя вводить пустое поле.
    2. Есть ограничение на ввод.
(поле email требует строку формата mail@mail.ru).
	1. При вводе незарегистрированной почты выводится сообщение, что пользователь не найден.
- Поле “Пароль”:
    1. Поле “Пароль” выдаёт предупреждение при вводе менее 8-ми символов..
    2. Нельзя вводить пустое поле.
    
- Кнопка “Назад”:
	1. Возвращает на предыдущую страницу.
- Кнопка “Войти”:
	1. При корректном вводе переводит на страницу https://bmstusa.ru.
	2. BUG: При вводе некорректного пароля и последующего нажатия на кнопку выводится сообщение “Пользователь не найден” вместо сообщения о неправильном пароле.
	
	![alt text](https://i.ibb.co/HDtrtQc/Login.jpg)
- Кнопка “Регистрация”:
	1. Переводит на страницу https://bmstusa.ru/signup.

### Хедер
Присутствует на всех страницах, кроме регистрации и логина.
- Лого “BMSTUSA”:
	1. При нажатии редиректит на https://bmstusa.ru/.
- Поле “Поиск”:
    1. При непрерывном вводе текста в поле ничего не происходит.
    2. При вводе текста в поле и остановкой набора текста, если пользователь находится на главной странице, мероприятия обновляются, иначе происходит редирект на главную страницу с соответствующими мероприятиями.
    3. BUG: Верхняя граница длины строки отсутствует.
    4. BUG: При вводе 1-го пробела пропадает самое популярное мероприятие.
	### До: 
	![alt text](https://i.ibb.co/gmQKJdS/beforeM.jpg)
	### После:
	![alt text](https://i.ibb.co/HgsG2qD/AfterM.jpg)

Для неавторизованного пользователя:
- Кнопка “Войти”:
	1. При нажатии редиректит на https://bmstusa.ru/login.
- Кнопка “Регистрация”:
	1. При нажатии редиректит на https://bmstusa.ru/signup.

Для авторизованного пользователя:
- Кнопка “Уведомления”:
    1. При нажатии накладывается оверлей на контент страницы, под хедером появляется список уведомлений. С контентом под оверлеем взаимодействовать нельзя.
    2. При нажатии на уведомление из списка происходит редирект на контент уведомления (на профиль пользователя при подписке или на мероприятие при приглашении/создании).
    ### Уведомление о подписке:
    ![alt text](https://i.ibb.co/MprXtK0/notification-subscribe.jpg)
    ![alt text](https://i.ibb.co/1LH45zw/subscribe-result.jpg)
    ### Уведомление о приглашении на мероприятие:
    ![alt text](https://i.ibb.co/MBVxmQK/notification-invite.jpg)
    ![alt text](https://i.ibb.co/5YSCFXL/invite-result.jpg)
    3. При нажатии вне списка уведомлений, оверлей и список пропадает.
- Кнопка “Аватар”:
	1. При нажатии накладывается оверлей и появляются кнопки:
- Кнопка “Профиль”:
	1. При нажатии переходит на профиль авторизованного пользователя.
- Кнопка “Создать мероприятие”:
	1. При нажатии переходит на https://bmstusa.ru/create.
- Кнопка “Выйти из аккаунта”:
	1. При нажатии разлогинивает пользователя и переходит на https://bmstusa.ru/. 

### Страница профиля
https://bmstusa.ru/user?id={UserID}
- Кнопка “Созданное”:
	1. Выдаёт созданные пользователем мероприятия (При отсутствии таких, выдаёт сообщение “Список пуст”).
- Кнопка “Избранное”:
	1. Выдаёт мероприятия, добавленные пользователем в Избранное (При отсутствии таких, выдаёт сообщение “Список пуст”).
- Кнопка “Подписки”:
	1. Выдаёт пользователей, на которых подписан текущий пользователь (При отсутствии таких, выдаёт сообщение “Список пуст”).
- Кнопка “Подписчики”:
	1. Выдаёт пользователей, которые подписаны на текущего пользователя (При отсутствии таких, выдаёт сообщение “Список пуст”).
- Кнопка “Карандаш”:
	1. Открывает меню редактирования профиля.

### Редактирование профиля
https://bmstusa.ru/user?id={UserID}
- Поле “Имя”:
    1. Есть ограничение на ввод некорректных символов. (Имена должны содержать только буквы, но имена с дефисом валидны)
    2. BUG: При вводе более 30-ти символов имя заходит за пределы активной области.
    ![alt text](https://i.ibb.co/SJ2Wvp2/all.jpg)
    3. Нельзя вводить пустое поле.
    4. BUG: Буква ё не считается буквой в полях ввода, следовательно не проходит контроль.
    ![alt text](https://i.ibb.co/pdLv7c1/Yo.jpg)
- Поле “Фамилия”:
    1. Выдаёт предупреждение на ввод некорректных символов
       (Фамилии должны содержать только буквы, но фамилии с дефисом валидны).
    2. BUG: При вводе более 30-ти символов фамилия заходит за пределы активной области.
    3. Нельзя вводить пустое поле.
    4. BUG: Буква ё не считается буквой в полях ввода, следовательно не проходит контроль.
    #### Баги аналогичны багам в пункте выше, поэтому скриншоты опущены.
- Поле “О себе”:
    1. BUG: При вводе очень длинной строки информация заходит за пределы активной области.
    #### Скриншот выше.
    2. Есть ограничение на длину символов (150).
- Кнопка “Фотография”:
    1. Открывает файловый менеджер для выбора изображения на аватар.
    2. Есть ограничения на тип файла (Не показываются недоступные типы).
    3. BUG: После выбора фотографии остаётся надпись “Новое фото не выбрано”.
	
    ![alt text](https://i.ibb.co/njDkKL0/photo.jpg)
- Кнопка “Отмена”:
    1. Возвращает на страницу профиля.
- Кнопка “Сохранить”
    1. Применяет введённые изменения.
- Кнопка “Пароль”:
    1. Открывает меню смены пароля.
- Поля паролей:
    1. Аналогичны полям паролей, описанным в разделе "Регистрация".

    ![alt text](https://i.ibb.co/1KPN4Wh/passwb.jpg)
### Страница мероприятия
https://bmstusa.ru/events?id={EventID}
- Кнопка “Пригласить”:
    1. Пересылает неавторизованного пользователя на страницу https://bmstusa.ru/login.
    2. Показывает список друзей (при отсутствии таких выдает сообщение “Вам некого пригласить”).
    3. Поле с выбранным профилем окрашивается в серый цвет, кнопка Пригласить становится активной, т.е. окрашивается в голубой и становится доступной к нажатию (пользователи, которых нельзя пригласить на мероприятие, - те, кто уже были приглашены на данное мероприятие, или его создатель - недоступны для нажатия и выбора).
    4. После нажатия кнопки “Пригласить” выбранным пользователям приходит уведомление о приглашении.
  
       ![alt text](https://i.ibb.co/w7ZqJBP/image.png)
    5. К выбору доступны несколько пользователей.
- Кнопка “Поделиться ссылкой”:
    1. Показывает, что ссылкой на мероприятие можно поделиться, скопировав ее, или в социальных сетях ВКонтакте и Telegram.
    2. При нажатии на кнопку "Скопировать ссылку" успешность действия подтверждается иконкой “галочка”.
    3. При нажатии на кнопку "Поделиться во ВКонтакте" или "Поделиться в Telegram" открывается выбранный сервис и появляется возможность отредактировать пост.
- Кнопка “Добавить в избранное”:
    1. Пересылает неавторизованного пользователя на страницу https://bmstusa.ru/login.
    2. При нажатии на кнопку успешность действия подтверждается окрашиванием в оранжевый цвет, а мероприятие добавляется во вкладку “Избранное”.
- Кнопка “Редактировать мероприятие”:
    1. Доступна только для создателя мероприятия
    2. Открывает меню, состоящее из двух пунктов: “редактировать” и “удалить”.
    3. При выборе пункта “редактировать” пользователь перенаправляется на страницу https://bmstusa.ru/edit?id={EventID}.
    4. При выборе пункта “удалить” мероприятие удаляется, а пользователь перенаправляется в Личный кабинет во вкладку “Созданное”.
- Кнопка “Автор мероприятия”:
	1. Перенаправляет пользователя на страницу автора мероприятия.
- Кнопка “Категория мероприятия”:
	1. Перенаправляет пользователя на Главную страницу, где в качестве поискового фильтра указана категория со Страницы мероприятия.
- Кнопка “Тeг”:
	1. Перенаправляет пользователя на Главную страницу, где в качестве поискового фильтра указан нажатый Тег со Страницы мероприятия.

### Страница Создание мероприятия
https://bmstusa.ru/create
- Страница:
    1. Недоступна для неавторизованного пользователя. При попытке посетить страницу без авторизации пользователь будет перенаправлен на страницу https://bmstusa.ru/login.
- Поля “Название”, “Краткое описание”, “Подробное описание”:
  1. Пустое поле без фокуса - серое.
  2. Заполненное поле без фокуса - белое.
  3. При фокусе меняют цвет на белый, появляется фиолетовая рамка.
  4. Если поле заполнено корректно, оно становится белым с зеленой рамкой.
  5. Если поле заполнено некорректно, оно становится белым с красной рамкой. Под полем появляется описанная текстом ошибка.
  6. Для создания мероприятия поля должны быть обязательно заполнены.
  7. Поля имеют ограничения по количеству символов: название - 255 символов, краткое описание - 500 символов, подробное описание - 2200 символов. Поля запрещают ввод символов при достижении лимита. В случае превышения количества символов пользователь увидит сообщение об ошибке.
     
  ![alt text](https://i.ibb.co/QKfvPnB/image.png)
- Поле “Категория”:
    1. При нажатии появляется список доступных категорий
    2. Если категория выбрана, поле становится белым, список скрывается.
    3. Если категория не выбрана, поле серое с надписью “Выберите категорию”.
    4. Пустое поле без фокуса - серое.
    5. Заполненное поле без фокуса - белое.
    6. Для создания мероприятия поле обязательно должно быть заполнено.
    7. При фокусе меняют цвет на белый, появляется фиолетовая рамка.
    8. Если поле заполнено корректно, оно становится белым с зеленой рамкой.
    9. Если поле заполнено некорректно, оно становится белым с красной рамкой. Под полем появляется описанная текстом ошибка.
- Поле “Дата”:
    1. При фокусе меняет цвет на белый, появляется фиолетовая рамка.
    2. Если поле заполнено корректно, оно становится белым с зеленой рамкой.
    3. Если поле заполнено некорректно, оно становится белым с красной рамкой. Под полем появляется описанная текстом ошибка.
    4. Пустое поле без фокуса - серое.
    5. Заполненное поле без фокуса - белое.
    6. Дата может быть введена вручную. Если дата не соответствует формату дд.мм.гггг, поле будет считаться заполненным некорректно, пользователь увидит под полем сообщение об ошибке.
    7. При нажатии на иконку “календарь”, открывается календарь, где можно выбрать дату. Текущая дата помечена оранжевым цветом. Выбранная пользователем дата обводится в оранжевый круг. При нажатии на кнопку “ОК” календарь закрывается. При нажатии на область вокруг календарь закрывается. При выборе даты календарь закрывается.
    8. BUG: На календаре можно выбрать дату, предшествующую текущей в данном месяце.

    ![alt text](https://i.ibb.co/BV1Rt53/image.png)
    
    ![alt text](https://i.ibb.co/ySBJT2y/image.png)
    
    ![alt text](https://i.ibb.co/JjbnmFr/image.png)
    
    9. Для создания мероприятия поле должно быть обязательно заполнено.
    10. Создать мероприятие в прошлом нельзя, пользователь увидит сообщение об ошибке.
- Поле “Адрес”:
    1. Незаполненное поле содержит надпись “Укажите адрес”.
    2. Для создания мероприятия поле должно быть обязательно заполнено.
    3. При нажатии на поле открывается попап с картой.
        - Карта:
            1. Поле Адрес при фокусе меняет цвет на белый, появляется фиолетовая рамка. В остальное время поле серое.
            2. При вводе адреса в поле Адрес выпадает список предложенных адресов. При выборе пункта из этого списка адрес записывается в поле ввода, а на карте появляется геометка.
            3. Кнопка Сохранить подтверждает выбранный адрес и закрывает попап. Если адрес не был распознан, пользователь увидит сообщение об ошибке “Адрес не найден”, попап останется открытым.
            4. Кнопка Отмена закрывает попап.
    4. Если адрес, выбранный в попапе Карта, был корректный, он будет вписан в поле Адрес на странице Создание мероприятия.
    5. BUG: Если длина адреса больше длины поля, его нельзя будет увидеть целиком.
- Поле “Теги”:
    1. При фокусе меняет цвет на белый, появляется фиолетовая рамка.
    2. Если поле заполнено корректно, оно становится белым с зеленой рамкой.
    3. BUG: Если поле заполнено некорректно, под полем появляется описанная текстом ошибка, но его рамка не окрашивается в красный.
    4. Пустое поле без фокуса - серое.
    5. Заполненное поле без фокуса - белое.
    6. Тег может состоять только из одного слова и содержать исключительно буквы и/или цифры.
    7. Чтобы добавить тег, пользователь может нажать клавишу Enter или нажать на иконку “плюс”. Добавленный трек отрисуется под полем. Чтобы удалить тег, надо навести на него и нажать появившуюся иконку “крестик”.
    8. К одному мероприятию не может быть добавлено больше 6 тегов. Если пользователь попытается добавить седьмой, то увидит сообщение об ошибке.
    9. У тега есть максимальная допустимая длина - 30 символов. Поле запрещает ввод символов при достижении лимита.
- Поле “Фотография”:
    1. При нажатии на иконку “фото” открывается окно выбора файла для загрузки.
    2. Когда файл выбран, надпись “Не выбрано” заменяется на надпись “Удалить фото”. Фотография показывается под полем в уменьшенном формате.
    3. При нажатии на “Удалить фото” фото пропадает, надпись снова заменяется на “Не выбрано”.
    4. Фото не может превышать размера в 5 Мб, если фото весит больше, пользователю показывается ошибка в текстовом виде.
    5. BUG: Если удалить фото, ошибка не исчезает.
- Кнопка “Сохранить”:
    1. При нажатии валидирует поля. Если ошибок нет, то пользователь попадает на страницу только что созданного мероприятия. Если ошибки есть, пользователь видит их под соответствующими полями, поля остаются заполненными. 
- Кнопка “Отмена”:
    1. Возвращает пользователя на предыдущую страницу.

### Страница Редактирование мероприятия
https://bmstusa.ru/edit?id={EventID}

Пункты, описанные для страницы Создание мероприятия, действуют и для этой страницы, помимо этого для страницы Редактирование мероприятия действуют следующие пункты:
- Страница:
    1. BUG: Если пользователь не является автором мероприятия, при попытке перейти по ссылке, он будет перенаправлен на страницу https://bmstusa.ru/login. При этом он будет перенаправляться на эту страницу при каждой попытке и не увидит сообщения о том, что права на редактирование ограничены.
    ### До:
    ![alt text](https://i.ibb.co/W5vkzSR/edit.jpg)
    ### После (Авторизоваться не получится):
    ![alt text](https://i.ibb.co/hCs19HB/logined.jpg)

- Поля “Категория”, “Название”, “Краткое описание”, “Подробное описание”, “Дата”, “Теги”:
    1. Поля остаются серыми до изменения или нажатия кнопки Сохранить, даже если в них содержится текст.
- Поле “Дата”:
    1. BUG: Если пользователь попытается редактировать мероприятие, которое уже завершилось до текущей даты, то при сохранении поле будет отмечено некорректным, пользователю необходимо будет переопределить дату на доступную.

    ![alt text](https://i.ibb.co/vcgjzNn/editDate.jpg)
- Поле “Фотография”:
    1. BUG: Если заменить фотографию, а потом удалить ее, то измененное мероприятие будет иметь фото, которое имело до редактирования, т.е. фотография не удалится.
    ### До:
    ![alt text](https://i.ibb.co/d0dZj2P/delete.jpg)
    ### После(Не удалено фото, осталось старое):
    ![alt text](https://i.ibb.co/85xvFpP/oldPhoto.jpg)

### Главная страница 
https://bmstusa.ru/

Боковая панель с фильтрами:
- Кнопки “Тусовки”...”Обучение”:
    1. При нажатии страница обновляется, и показываются только те мероприятия, которые имеют указанную на кнопке категорию или соответствуют другим параметрам фильтра.
    2. При повторном нажатии страница обновляется и фильтр по категории сбрасывается.
    3. Может быть нажата только одна кнопка категории.
- Поле “Тег”:
    1. Нельзя вводить пустое поле.
    2. Нельзя вводить поле, состоящее только из пробелов
    3. BUG: Нет ограничения на длину тега. При вводе длинного тега, поле ввода расширяется, и, вместе с тем, расширяется боковая панель и главная страница.

       ![alt text](https://i.ibb.co/1KyHQq4/bug.jpg)
    4. Тегов может быть неограниченно много.
    5. При попытке добавить тег, который был указан ранее, тег не добавляется. Вместо этого временно меняет свой цвет блок со старым тегом.
- Кнопка “+”:
    1. При нажатии отображает введенный в поле “Тег” тег снизу от поля.
    2. Поле “Дата”:
    3. При нажатии отображается календарь.
- Календарь:
    1. При нажатии на дату она отображается в поле “Дата”.
    2. При нажатии на треугольники “Влево” или “Вправо” меняется месяц.
    3. При выборе даты страница обновляется, и показываются только те мероприятия, которые проходят в указанную дату или соответствуют другим параметрам фильтра.
    4. В фильтре может быть указана только одна дата.
- Поле “Город”:
    1. При нажатии на поле выдвигается список с городами, в которых проходят мероприятия.
    2. При нажатии на один из городов страница обновляется, и показываются только те мероприятия, которые проходят в данном городе или соответствуют другим параметрам фильтра.
    3. В фильтре может быть указан только один город.
	
Блок с мероприятием:
- Картинка с фотографией мероприятия и название мероприятия:
	1. При нажатии перекидывает на страницу мероприятия https://bmstusa.ru/events?id={EventID}.
- Кнопка “Добавить в избранное”:
    1. При нажатии перекидывает на страницу авторизации https://bmstusa.ru/login, если пользователь не авторизован.
    2. При нажатии добавляет мероприятие в избранное и меняет свой цвет, если пользователь авторизован.
- Кнопка “Тег”:
    1. Добавляет в панель фильтров тег, указанный на кнопке. Производится фильтрация по данному тегу.
