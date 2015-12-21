## uLogin - виджет авторизации через социальные сети

Contributors: ulogin  
Donate link: https://ulogin.ru/  
Tags: ulogin, login, social, authorization  
Requires at least: 3.0  
Tested up to: 4.4  
Stable tag: 2.1.2  
License: GNU General Public License, version 2  
Форма авторизации uLogin через социальные сети. Улучшенный аналог loginza.  

## Описание

uLogin — это инструмент, который позволяет пользователям получить единый доступ к различным Интернет-сервисам без необходимости повторной регистрации,
а владельцам сайтов — получить дополнительный приток клиентов из социальных сетей и популярных порталов (Google, Яндекс, Mail.ru, ВКонтакте, Facebook и др.)

## Установка

1. Зайдите в административную панель сайта WordPress.
1. В разделе "Плагины" нажмите кнопку "Добавить новый".
1. В строке поиска впишите и найдите ulogin.
1. Установите и активируйте плагин. Плагин заработает сразу после активации с настройками по умолчанию.

Более детальную информацию смотрите [здесь](https://ulogin.ru/help.php#cms-wp)  
Вы можете создать свой виджет и редактировать его самостоятельно на сайте [ulogin.ru](http://ulogin.ru/).  

Для создания виджета необходимо:

1. Зайти в Личный Кабинет (ЛК) на сайте [ulogin.ru](http://ulogin.ru/)
1. На вкладке "Виджеты" добавить новый виджет
1. **Внимание:** Для работы модуля uLogin в ЛК необходимо включить в обязательных полях профиля поле Еmail
1. В настройках плагина необходимо указать ID виджета в соответствующих полях

*Для ручного вывода панели авторизации в любом месте темы используйте код*

    `<?php echo get_ulogin_panel(); ?>`

    `/**
    * int $panel - номер uLogin панели, соответствует указанным в настройках плагина полям с ID (значение 0 - для первого плагина, 1 - для второго)
    * bool $with_label - указывает, стоит ли отображать строку типа "Войти с помощью:" рядом с виджетом (true - строка отображается)
    * bool $is_logining - указывает, отображать ли виджет, если пользователь залогинен (false - виджет скрывается)
    * string $id - id для div-панели (если не задан - генерируется автоматически)
    */
    function get_ulogin_panel($panel = 0, $with_label = true, $is_logining = false, $id='')`

*Для ручного вывода блока "Синхронизация аккаунтов" в любом месте темы используйте код*

    `<?php ulogin_synchronisation_panel(); ?>`

    `/**
    * @param int $user_id - ID пользователя (если не задан - текущий пользователь)
    */
    function ulogin_synchronisation_panel($user_id = 0)`

*Для вывода списка аккаунтов пользователя используйте код*

    `<?php echo get_ulogin_user_accounts_panel(); ?>`
    `/**
    * int $user_id - ID пользователя (если не задан - текущий пользователь)
    */
    function get_ulogin_user_accounts_panel($user_id = 0)`

## Частые вопросы и ответы

#### Как создать свой виджет?

1. Зайти в Личный Кабинет (ЛК) на сайте [ulogin.ru](http://ulogin.ru/)
1. На вкладке "Виджеты" добавить новый виджет
1. Редактировать виджет ([редактирование](http://ulogin.ru/help.php#cody))

*Внимание:* Для работы модуля uLogin в ЛК необходимо включить в обязательных полях профиля поле Еmail

#### Где взять ID для формы входа и для формы комментариев?
Если Вы успешно создали виджет на сайте **uLogin.ru**, то нужный Вам ID Вы сможете найти в [личном кабинете](http://ulogin.ru/lk.php) на вкладке "Виджеты" в полях *"uLogin ID"*.

#### Возникает ошибка "Необходимо указать email в возвращаемых полях uLogin". Что означает?
В [личном кабинете](http://ulogin.ru/lk.php) должно быть включено в обязательных полях профиля поле Еmail. Данная ошибка возникает, если это требование не выполнено.

## Upgrade Notice
Улучшено время входа пользователя в систему.
Добавлена возможность уведомления по почте администратора сайта о регистрации нового пользователя и отправка пользователю письма с логином и паролем для авторизации.

## Changelog

#### 2.1.2
* Добавлен вызов хука ulogin_registration после успешной регистрации пользователя через сосцеть
* Добавлена поддержка параметра redirect_to для возврата на конкретную страницу после авторизации

#### 2.1.1
* Улучшение совместимости с плагином предыдущей версии.

#### 2.1.0
* Добавлен функционал управления отображением аватарами соцсетей в настройках плагина. Для отключения отображения аватар соцсетей для любого типа "Аватар по умолчанию" необходимо в настройках плагина (Настройки->Плагины->uLogin) снять соответствующую галочку.
* Улучшена совместимость с плагином WP User Avatar.
* Улучшена совместимость с плагином BuddyPress.
* Исправлен баг c редиректом во время ajax-вызова виджета uLogin.
* Исправлен баг с аватарками групп плагина BuddyPress.
* Исправлен баг c повторной инициализацией виджета.
* Исправлен баг генерации логина при авторизации.
* Исправлен баг c label.

#### 2.0.13
* Добавлена функция "Деактивации" и "Удаление" плагина.
* Исправлен баг label "Войти с помощью:"
* Исправлен баг с аватарками BuddyPress
* Проведён небольшой рефакторинг, исправлены мелкие баги и notice.

#### 2.0.12
* Улучшено время входа пользователя в систему.
* Добавлена возможность уведомления по почте администратора сайта о регистрации нового пользователя и отправка пользователю письма с логином и паролем для авторизации.
* Проведён небольшой рефакторинг, исправлены баги.

#### 2.0.11
* Улучшена совместимость с плагином BuddyPress. Для отображения аватарок соцсетей необходимо в панели администратора (Настройки->Обсуждения) в списке "Аватар по умолчанию" выбрать пункт uLogin.
* Улучшена совместимость с плагином Simple:Press. Исправлено кривое отображение аватарки гостя.

#### 2.0.10
* Срочное исправление

#### 2.0.8
* Добавлена поддержка плагина WP User Avatar.
Аватар, полученный с помощью uLogin, устанавливается как аватар по умолчанию для выбранного пункта "WP User Avatar" из списка "Аватар по умолчанию".
* В панели администратора на странице настроек плагина выведена возможность отключения сохранения ссылки на профиль пользователя в соцсети.
При отключении этого пункта поле "Сайт" в профиле пользователя не будет заполняться автоматически при авторизации.
Если поле "Сайт" было заполнено раннее, то при авторизации через uLogin (при отключенном пункте "Сохранять ссылку на профиль") данное поле будет очищаться при полном соответствии с данными от uLogin.
* На странице настроек плагина выведено поле "uLogin ID форма для профиля пользователя".
* Изменена страница настроек плагина в панели администратора.
* Добавлена ссылка на страницу настроек из списка плагинов.
* Хук "comment_form_before_fields" заменён на "comment_form_top".

#### 2.0.7
* Оптимизирована проверка наличия аватара Gravatar.
* Совместимость с WordPress 4.1

#### 2.0.6
* Критичный фикс

#### 2.0.5
* Иконки провайдеров "Привязанные аккаунты" теперь берутся с сервера ulogin.ru
* В панели администратора Настройки->Обсуждения в список "Аватар по умолчанию" добавлен пункт uLogin.
При выборе этого пункта у пользователей устанавливаются аватарки, загруженные с помощью плагина uLogin.
При выборе других пунктов будут отображаться аватарки в выбранном стиле.
* Реализована поддержка аватар Gravatar. Т.е., если у пользователя установлено изображение на сервере Gravatar.com, аватарка пользователя меняться не будет.
* Проведён небольшой рефакторинг, исправлены баги.

#### 2.0.4
* Совместимость с WordPress 4.0
* Улучшена совместимость модуля с другими продуктами (возникала ошибка при активации плагина)

#### 2.0.3
* Исправлена ошибка регистрации таблицы в БД
* Исправлена ошибка генерации никнейма

#### 2.0.2
* Добавлена возможность вывода формы "Синхронизация аккаунтов" в любом месте с помощью функции ulogin_synchronisation_panel()
* Изменён внешний вид значков привязанных аккаунтов социальных сетей в форме синхронизации аккаунтов
* Реализована совместимость с плагином BuddyPress (аватарки, синхронизация аккаунтов в профиле пользователя)
* Исправлена ошибка возникновения дублирования привязанных аккаунтов

#### 2.0.1
* Исправлена ошибка с непредсказуемым редиректом после авторизации
* Исправлена js-ошибка на странице профиля пользователя (не работала синхронизация аккаунтов)

#### 2.0
* Реализована синхронизация учётных записей пользователя.
* Реализована настройка виджета из Личного кабинета uLogin.
* Добавлена функция get_ulogin_panel() для ручного вывода панели.
* Ряд других незначительных изменений.

#### 1.8.2
* Добавлен возврат на исходную страницу после авторизации

#### 1.8.1
* Добавлена панель uLogin для формы регистрации;
* Расширен способ получения пользовательских данных от uLogin(curl или file_get_contents);
* В профиль пользователя корректно добавляется ссылка на страницу в соц. сети.

#### 1.8
* Добавлена страница настроек в административной панели, добавлена панель на форму логина.

#### 1.7
* Исправление ошибок, неограниченное количество сущностей uLogin на странице

#### 1.6
* Добавлена поддержка плагина Simplemodal Login Form

#### 1.5
* Исправлена генерация пароля на wp_generate_password()

#### 1.4
* Исправлена ошибка, возникающая из-за динамического подключения скрипта

#### 1.3
* Исправлена ошибка, возникающая, если email уже был в базе.

#### 1.2
* Исправлен js код.
* Добавлена функция ulogin_panel() для ручного вывода панели.

#### 1.1
* Проблемы с SVN

#### 1.0
* Релиз.
