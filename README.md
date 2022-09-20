# Задачі на тестове

У завданні не оцінюватиметься краса та дизайн. Бо дизайну нема.
Головне як написаний код та як він структурований.

Зробить максимальну кількість завдань за відведений проміжок часу.
Всюди використовувати Composition API та максимально використовувати код (DRY підхід).
Використання принципів SOLID стане великим плюсом.
Логіку потрібно написати самому без сторонніх ліб та реалізацій.

## Структура репозіторія:
Структура репозиторію наближена до реального проекту,
але виділені непотрібні для цього завдання елементи.

/src
  /shared — глобальні елементи
  /entities — всі сущності, типи, стори повинні знаходитися тут (Entity)
  /feature — тут знаходятся компонени з простою логікою (Use Case)
  /widgets — тут знаходятся саомдостатні блоки з набором компонентів. наприклад шапка додатку (header) чи нижня частина сторінки (footer)
  /pages — сторінки додатку
  /app
    /nuxt-configs — конфіги для nuxt.config.ts

## Як здавати завдання
Потрібно створити окрему гілку та назвати її у форматі `{lastname}_{firstname}`.
Після того як ви закінчите завдання або закінчиться час на нього зробіть пуш у цю гілку.

## Задачі

1) Додати на сторінку `/index`, в верхню частину, блок навігації. В блоці навигації 3 лінки `/auth/login`, `/auth/secret` і `/bug`. Шляхи роутінгу розтошовувати в констані `@/src/shared/config/routeNav.ts`

2) Додати блок навігації із пунтка (1) на сторінку `/bug`. Щоб можно було просто переходити між сторінками.

3) Пофіксити баг на сторінці `/bug`. Баг з'являєтся коли натискаєш на кнопку "Show Name". Повинна відображатися назва конкретного роутінга.

4) Створити сторінку `/auth/login`. На цій сторінці відсутній блок навігації. Тут потрібно зробити форму з 3 елементами:
– Поле введення пошти.
- Поле введення пароля. Мінімум 3 символи, а максимум 20. Пароль повинен мати хоча б одну велику літеру, хоча б одну малу літеру, хоча б одну цифру і хоча б один спецсимвол (~!@#$&%-_'")
- кнопка `Login`

Поля мають бути з валідацією, а кнопка `Login` не активна, якщо форма невалідна. Поле повинно показувати, які помилки виникли після початку взаємодії з ним. Якщо поле не валідно бордер повинен стати червоним.

5) Логіка обробки сабміту форми із крока (4).

Після натискання на кнопку `Login`. Зробити функцію, яка перевірятиме пошту (`tester@test.com`) та пароль (`TesteR@007"`). Потім ця функція робитиме запит на сервер. Замокуватиме перевірку та відповіді сервера. Сервер повертатиме наступні відповіді:
- якщо пошта та пароль коректні: {success: true}
- якщо пошта або пароль не коректні {seccess: false, error: 'login or password incorrect'}

Якщо поле чи пароль не коректні, показувати над формою плашку з помилкою з поля `error`. Пароль видили із поля вводу, а пошту залишата.

Після успішної аутентіфікації зберігати данні користувача, на час сессії браузера.
І переадресувати на сторінку `/auth/secret`

6) Створити сторінку `/auth/secret`.

Сторінка доступна лише авторизованим користувачам. Якщо користувач не авторизований тоді його переадресую на `/index` сторінку.

На сторінці знаходяться такі елементи:
- Блок навігації зроблений у пункті (1)
- Відображення пошти користувача в тегі h1
- Форма редагування

Форма редагування складається з:
- Поля введення з поштою авторизованого користувача
- Кнопка `Save`.

Форма дозволяє редагувати пошту користувача та зберігати її.
Принцип валідації такий самий як у пункті (4):
- Кнопка `Save` не активна доки форма не валідна
- Поле з поштою відображає помилки як у пункті (4)

7) Доработать блок навигации, сделанный в пункте (1).

- Додати відображення пошти авторизованого користувача. Якщо користувач авторизований тоді відображати пошту деб не був блок навігації.
- Додати кнопку `Logout`. Відображається лише за наявності авторизованого користувача. При натисканні розлогінює користувача. І він не має доступу до сторінки `/auth/secret` доки не почнеться знову.
