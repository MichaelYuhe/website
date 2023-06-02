---
next: ./guide.md
---

# Що таке плагін?

Ми хочемо, щоб grammY був компактним та мінімалістичним, але мав можливість розширення.
Чому?
Тому що не всі використовують все!
Плагіни розроблені як додаткові функціональні можливості, що додаються до зазначених частин програмного забезпечення.

## Плагіни в grammY

Деякі плагіни **вбудовані** безпосередньо до бібліотеки grammY, оскільки ми вважаємо, що вони потрібні багатьом ботам.
Це полегшує їх використання новими користувачами без необхідності встановлювати новий пакет.

Більшість плагінів публікуються разом з основним пакетом grammY, ми називаємо їх **офіційними** плагінами.
Пакети встановлюються з `@grammyjs/*` на npm і публікуються під організацією [@grammyjs](https://github.com/grammyjs) на GitHub.
Ми координуємо їхні релізи з релізами grammy і стежимо за тим, щоб все працювало злагоджено.
Кожен розділ документації до офіційного плагіна має назву пакета в назві.
Наприклад, плагін [плагін для конкурентності (runner)](./runner.md) (`runner`) потрібно встановити за допомогою `npm install @grammyjs/runner`.
Якщо ви використовуєте Deno, а не Node.js, вам слід імпортувати плагін з <https://deno.land/x/>, тобто з файлу `mod.ts` модуля `grammy_runner`.

Існує також низка **сторонніх** плагінів.
Їх може публікувати будь-хто.
Ми не надаємо жодних гарантій, що вони є актуальними, добре задокументованими або працюють разом з іншими плагінами.
Ви також можете розмістити свій власний плагін на сайті, щоб про нього дізналося більше людей.

## Огляд

Ми склали для вас стислий огляд з короткими описами кожного плагіна.
Встановлювати плагіни весело і легко, тому ми хочемо, щоб ви знали, які плагіни у нас для Вас є.

> Натисніть на будь-яку назву пакета, щоб дізнатися більше про відповідний плагін.

| Плагін                      | Пакет                                                 | Опис                                                                        |
| --------------------------- | ----------------------------------------------------- | --------------------------------------------------------------------------- |
| Sessions                    | _вбудовано_                                           | Зберігання даних користувачів в базі                                        |
| Inline and Custom Keyboards | _вбудовано_                                           | Спрощення створення вбудованих і кастомних клавіатур                        |
| Auto-retry                  | [`auto-retry`](./auto-retry.md)                       | Автоматичне оброблення лімітів                                              |
| Conversations               | [`conversations`](./conversations.md)                 | Створюйте потужні діалогові інтерфейси                                      |
| Emoji                       | [`emoji`](./emoji.md)                                 | Спрощене використання емодзі в коді                                         |
| Files                       | [`files`](./files.md)                                 | Легка робота з файлами                                                      |
| Hydration                   | [`hydrate`](./hydrate.md)                             | Виклик методів в обʼєктах, що повертаються з викликів API                   |
| Internationalization        | [`i18n`](./i18n.md) or [`fluent`](./fluent.md)        | Дозвольте вашому боту розмовляти кількома мовами                            |
| Interactive Menus           | [`menu`](./menu.md)                                   | Створюйте динамічні меню з кнопками та гнучкою навігацією                   |
| Parse Mode                  | [`parse-mode`](./parse-mode.md)                       | Спрощене форматування повідомлень                                           |
| Rate Limiter                | [`ratelimiter`](./ratelimiter.md)                     | Автоматичне обмеження користувачів, які спамлять вашого бота                |
| Router                      | [`router`](./router.md)                               | Направляйте повідомлення в різні частини коду                               |
| Runner                      | [`runner`](./runner.md)                               | Багатопоточне довге очікування (long polling) з масштабуванням              |
| Stateless Question          | [`stateless-question`](./stateless-question.md)       | Створення діалогів без використання сховища даних                           |
| Flood Control               | [`transformer-throttler`](./transformer-throttler.md) | Створення черги викликів до API для запобігання надмірної кількості запитів |

У нас також є кілька сторонніх плагінів!
Ви можете знайти їх у навігаційному меню в розділі _Плагіни_ > _Сторонні_.
Не забудьте перевірити їх теж!

## Типи плагінів в grammY

Все, що блищить — золото, чи не так?
Що ж, золото іншого роду!
grammY може використовувати переваги двох типів плагінів: _проміжного обробника_ та _перетворювачі_.
Простіше кажучи, плагіни в grammY повертають або функцію проміжного обробника, або функцію-перетворювач.
Поговоримо про відмінності.

### Тип I: Плагіни проміжного обробника

[Проміжний обробник](../guide/middleware.md) — це функція, яка здійснює обробку вхідних даних у різноманітних формах.
Плагіни проміжного обробника встановлюються в бота, як ви вже здогадалися, як проміжний обробник.
Це означає, що вам потрібно встановлювати їх через `bot.use`.

### Тип II: Плагіни-перетворювачі

[Перетворювач](../advanced/transformers.md) — це повна протилежність проміжного обробника!
Це функція, яка обробляє вихідні дані.
Плагіни-перетворювачі встановлюються в бота, як ви вже знову здогадалися, як функції-перетворювачі.
Це означає, що вам потрібно встановлювати їх через `bot.api.config.use`.

## Створюйте власні плагіни

Якщо Ви хочете створити плагін та поділитись ним з іншими користувачами (навіть опублікувавши на офіційному сайті grammY), ми маємо для Вас [корисний посібник](./guide.md), з яким Ви можете ознайомитися.

## Ідеї для нових плагінів

Ми збираємо ідеї для нових плагінів [на GitHub у цій Issue](https://github.com/grammyjs/grammY/issues/110).