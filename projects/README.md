# Telegram-бот записів для бʼюті-студії

Telegram-бот на n8n для домашньої студії з двома майстринями: манікюр і педикюр, масаж. Збирає заявки з форми, веде спільний розклад у Google Calendar і Google Sheets, нагадує клієнткам і майстриням про візити.

Бот щодня працює в реальній студії. Я в ній і розробниця бота, і майстриня масажу.

## Яку проблему вирішує

- Записи приходили в Instagram, Telegram і дзвінками, розклад тримався в памʼяті та скріншотах.
- Спільного розкладу не було, тож легко було поставити двох клієнток до однієї майстрині на один час.
- Нагадування залежали від того, чи хтось згадає їх надіслати.
- Побажання клієнток губились у переписці.

## Як працює

1. Клієнтка заповнює форму: імʼя, телефон, нік у Telegram, послуга, коли зручно, коментар.
2. Бот дає заявці ID і надсилає картку потрібній майстрині за типом послуги.
3. Майстриня домовляється з клієнткою і відповідає боту датою й часом звичайними словами: `25.10 14:00`, `завтра 16:00`.
4. Бот рахує тривалість за процедурою, перевіряє слот саме цієї майстрині і створює подію в Google Calendar та рядок у Google Sheets.
5. Клієнтка отримує підтвердження з кнопками «Перенести» і «Скасувати». Кнопки надсилають запит адмінкам, змінюють запис тільки вони.
6. Запис з Direct майстриня додає одним повідомленням: `завтра в 13:30 манікюр Оля 0671234567`. Groq (`openai/gpt-oss-120b`) витягує дату, час, процедуру, імʼя і телефон.
7. Кнопки «Сьогодні», «Завтра», «Тиждень», «Усі записи», «Вільні вікна», «Нові заявки». Щовечора о 21:00 бот надсилає розклад на завтра.
8. Нагадування: клієнтці за добу і за годину, обом майстриням за годину разом з нотатками до запису.
9. Картка запису `/n_ID`: дописати, замінити чи очистити нотатку, змінити телефон або час. Клієнтка нотатку не бачить.
10. Особисті нотатки: повідомлення з `!` зберігається з нагадуванням, `/notes` показує список, `/done_ID` закриває.

## Архітектура

Один воркфлоу, 69 нод, 4 тригери:

- Form Trigger: заявки
- Telegram Trigger: повідомлення і кнопки
- Schedule о 21:00: розклад на завтра
- Schedule кожні 15 хвилин: нагадування

Self-hosted n8n на PikaPods, без платних API.

## Інженерні деталі

- Зайнятість рахується окремо для кожної майстрині: подія в календарі несе в описі майстриню, ID і мітку «Записано через бота». Особисті події не блокують слот.
- Усі гілки складають повідомлення в масив, Split Out розгортає його, Switch обирає клавіатуру. Нова гілка не потребує своїх Telegram-нод.
- Прапорці нагадувань у таблиці не дають надіслати нагадування двічі. При переносі вони скидаються.
- Structured Output Parser з Groq не працює, тому відповідь AI розбирається в Code-ноді через `JSON.parse`.
- Google Sheets може повернути дату й час числом, код нормалізує обидва формати.

## Як запустити

1. Імпортуй `beauty-studio-booking-bot.json` в n8n.
2. Підключи credentials: Telegram, Google Sheets, Google Calendar, Groq (усі зараз `REPLACE_ME`).
3. Заміни плейсхолдери: `ADMIN_CHAT_ID_1`, `ADMIN_CHAT_ID_2`, `YOUR_SHEET_ID`, `BOOKINGS_SHEET_ID`, `NOTES_SHEET_ID`, `YOUR_CALENDAR_ID`, `YOUR_N8N_HOST`, `YOUR_BOT_USERNAME`.
4. Створи таблицю з колонками з ноди «Записати заявку» і лист «Нотатки».
5. Активуй воркфлоу.

## Скріншоти

![Воркфлоу в n8n](screenshots/workflow.png)
![Меню бота](screenshots/menu.png)
![Адмін-панель](screenshots/admin-panel.png)

Імена і телефони на скріншотах тестові. Реальні дані клієнток не публікуються.

---

# Telegram Booking Bot for a Beauty Studio

An n8n Telegram bot for a home studio with two masters: manicure and pedicure, and massage. It collects requests from a form, keeps a shared schedule in Google Calendar and Google Sheets, and reminds clients and masters about visits.

The bot runs in a real studio every day. I'm both the bot's developer and the studio's massage therapist.

## The problem

- Bookings came in through Instagram, Telegram and calls, and the schedule lived in memory and screenshots.
- There was no shared schedule, so it was easy to book two clients with the same master at the same time.
- Reminders went out only if someone remembered.
- Client requests got lost in chats.

## How it works

1. The client fills in a form: name, phone, Telegram handle, service, preferred time, comment.
2. The bot gives the request an ID and sends a card to the right master based on the service.
3. The master agrees on a time with the client and replies to the bot in plain words: `25.10 14:00`, `tomorrow 16:00`.
4. The bot works out the duration from the service, checks that master's slot, and creates a Google Calendar event and a Google Sheets row.
5. The client gets a confirmation with "Reschedule" and "Cancel" buttons. The buttons send a request to the admins, and only they change the booking.
6. A booking from Instagram DMs is added in one message: `tomorrow 13:30 manicure Olya 0671234567`. Groq (`openai/gpt-oss-120b`) extracts the date, time, service, name and phone.
7. Buttons for "Today", "Tomorrow", "Week", "All bookings", "Free slots", "New requests". Every evening at 21:00 the bot sends tomorrow's schedule.
8. Reminders: the client gets one a day before and one an hour before, both masters get one an hour before, with the booking notes.
9. Booking card `/n_ID`: add, replace or clear a note, change the phone or the time. The client doesn't see notes.
10. Personal notes: a message starting with `!` is saved with a reminder, `/notes` lists them, `/done_ID` closes one.

## Architecture

One workflow, 69 nodes, 4 triggers:

- Form Trigger: requests
- Telegram Trigger: messages and buttons
- Schedule at 21:00: tomorrow's schedule
- Schedule every 15 minutes: reminders

Self-hosted n8n on PikaPods, no paid APIs.

## Engineering details

- Availability is checked per master: each calendar event stores the master, the ID and a "booked via bot" tag in its description. Personal events don't block a slot.
- Every branch puts its messages into an array, Split Out unpacks it, and a Switch picks the keyboard. A new branch doesn't need its own Telegram nodes.
- Reminder flags in the sheet stop duplicates. A reschedule resets them.
- Structured Output Parser doesn't work with Groq, so the AI reply is parsed in a Code node with `JSON.parse`.
- Google Sheets can return dates and times as numbers, and the code handles both formats.

## Setup

1. Import `beauty-studio-booking-bot.json` into n8n.
2. Connect credentials: Telegram, Google Sheets, Google Calendar, Groq (all set to `REPLACE_ME` now).
3. Replace the placeholders: `ADMIN_CHAT_ID_1`, `ADMIN_CHAT_ID_2`, `YOUR_SHEET_ID`, `BOOKINGS_SHEET_ID`, `NOTES_SHEET_ID`, `YOUR_CALENDAR_ID`, `YOUR_N8N_HOST`, `YOUR_BOT_USERNAME`.
4. Create a sheet with the columns from the "Записати заявку" node and a "Нотатки" tab.
5. Activate the workflow.

## Screenshots

See the images above. Names and phone numbers are test data. No real client data is published.
