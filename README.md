# Leanback Launcher — New Generation

Лёгкий и гибкий лаунчер для **Android TV**, **Google TV** и **Amazon Fire TV**. За основу взят классический Leanback Launcher от Google, проект переписан на Kotlin и сильно расширен: каналы Android TV, недавние приложения, обои из интернета, заставка, погода, защита приложений и резервное копирование.

**[⬇️ Скачать последнюю версию](https://github.com/azimoff7007/Leanbackonfire/releases/latest)** · Android 5.1 и новее

<!-- Скриншоты: положите картинки в папку docs/ и раскомментируйте строки ниже
![Главный экран](docs/home.png)
![Подробности карточки канала](docs/channel-details.png)
-->

---

## ✨ Возможности

### 🏠 Главный экран
- Разделы **«Избранное»**, **«Видео»**, **«Музыка»**, **«Игры»** и **«Приложения»**: каждый можно включить или выключить и выбрать, сколько в нём строк.
- **Внешний вид баннеров:** масштаб 50–200 %, радиус скругления углов, цвет и толщина рамки выделения.
- **Генератор баннеров:** красивый баннер для любого приложения прямо на телевизоре — название, размер шрифта, иконка, выравнивание и неоновая подсветка.
- **Скрытие приложений**, в том числе нескольких сразу, и ручная сортировка баннеров пультом.
- **Нижняя строка** («Все приложения», «Каналы», «Настройки», «Обои», «Питание», сеть): порядок меняется долгим нажатием OK.
- **Встроенное меню всех приложений** (App Drawer) с сортировкой.

### 📺 Каналы и рекомендации
- **Каналы Android TV (Android 8+)**: ряды с контентом YouTube, Spotify, KinoTrend, Lampa и других приложений прямо на главном экране.
- **Подробности выбранной карточки:** название, дата выхода, страна и жанр, просмотры, длительность и описание на тёмном градиенте внизу экрана.
- **Порядок без перегрузки:** не больше 2 каналов от одного приложения на главном экране, до 10 горизонтальных или 20 вертикальных карточек в ряду, кнопка «Все» для перехода в приложение.
- **Боковое меню каналов** (кнопка «Каналы» или долгое нажатие ◀): включение, выключение, переименование и порядок каналов и приложений.
- **«Все каналы»:** экран со всеми каналами всех приложений, включая выключенные на главном экране.
- **Рекомендации на Android 5–7** работают как раньше, через уведомления приложений.

### 🔄 Недавние приложения
Двойное нажатие **«Домой»** открывает панель с приложениями, работающими в фоне: OK — открыть, удержание OK — закрыть, отдельная кнопка — «Закрыть все». Включается в «Настройке главного экрана».

### 🖼 Обои и заставка
- Свои обои или **обои из интернета** по категориям (природа, космос, машины, города, абстракции, аниме) в Full HD и 4K, с **автосменой** по расписанию.
- **Заставка** с задержкой запуска, таймером сна и быстрым запуском кнопкой «Назад».

### ☀️ Погода
Погода на главном экране по вашему местоположению или выбранному городу. Работает без регистрации ключей (Open-Meteo) и показывает последние данные, если пропал интернет.

### 🛡 Защита от удаления
Удаление приложений подтверждается **4-значным PIN-кодом**: дети или гости не удалят ничего случайно.

### ⚙️ И ещё
- **Резервное копирование:** настройки, порядок приложений, баннеры и обои в один файл; восстановление из любой папки, с флешки или SD-карты.
- **Язык системы** и **клавиатура** прямо из настроек лаунчера.
- **Меню питания:** отключение экрана и перезагрузка с пульта.
- **Проверка обновлений** на GitHub с полноэкранным журналом изменений.
- Интерфейс на **9 языках**: русском, английском, украинском, немецком, испанском, французском, итальянском, польском и китайском.

---

## 📥 Установка

1. Скачайте APK из раздела **[Releases](https://github.com/azimoff7007/Leanbackonfire/releases/latest)**.
2. Установите его на телевизор любым удобным способом: Downloader, Send Files to TV, флешка, ADB (`adb install Leanbacklauncher_vX.X.X-release.apk`).
3. Нажмите **«Домой»** на пульте и выберите Leanback Launcher.

Новые версии устанавливаются поверх старых, настройки сохраняются.

## 🔑 Разрешения через ADB

Часть возможностей требует разрешений, которые Android TV не позволяет выдать с экрана. Подключитесь к телевизору по ADB с компьютера (или через LADB / ADB Shell на самом ТВ) и выполните нужные команды. Готовые команды и QR-код есть в лаунчере: **Настройки → О приложении → Разрешения ADB**.

```bash
# Недавние приложения и статистика использования
adb shell appops set com.tv.leanback.launcher GET_USAGE_STATS allow

# Смена языка системы из настроек лаунчера
adb shell pm grant com.tv.leanback.launcher android.permission.CHANGE_CONFIGURATION

# Доступ к защищённым системным настройкам
adb shell pm grant com.tv.leanback.launcher android.permission.WRITE_SECURE_SETTINGS

# Рекомендации на Android 5–7 (чтение уведомлений приложений)
adb shell settings put secure enabled_notification_listeners com.tv.leanback.launcher/com.tv.leanback.launcher.recommendations.NotificationsServiceV4
```

## ❓ Частые вопросы

**Почему у приложения нет каналов?** Каналы создаёт само приложение, лаунчер только показывает их. Некоторые приложения публикуют каналы только для стандартного лаунчера Google или только после входа в аккаунт. Обычно помогает запустить приложение хотя бы один раз.

**Как показать больше каналов одного приложения?** Откройте боковое меню каналов, разверните приложение и включите нужный канал. На главном экране помещается до 2 каналов одного приложения, а все остальные доступны в «Всех каналах».

---

<details>
<summary>🇬🇧 English</summary>

## Leanback Launcher — New Generation

A light and flexible launcher for **Android TV**, **Google TV** and **Amazon Fire TV**, based on Google's classic Leanback Launcher, rewritten in Kotlin and greatly extended.

**[⬇️ Download the latest version](https://github.com/azimoff7007/Leanbackonfire/releases/latest)** · Android 5.1 and newer

### Features
- **Home screen:** Favorites, Video, Music, Games and Apps rows with configurable size; banner scale (50–200 %), corner radius, focus frame color and width; an on-device **banner generator**; hiding and sorting apps; a reorderable bottom row; a built-in App Drawer.
- **Android TV channels (Android 8+):** rows from YouTube, Spotify and other apps, with **details of the focused card** (title, release date, genre, views, duration, description) at the bottom of the screen. At most 2 channels per app on the home screen and up to 10/20 cards per row keep it clean. A side menu manages, renames and reorders channels; **All channels** lists everything. Notification recommendations still work on Android 5–7.
- **Recent apps** on a double **Home** press: open, close or close all background apps.
- **Wallpapers and screensaver:** your own or online wallpapers (Full HD / 4K) with auto-change; screensaver with start delay, sleep timer and a Back-button shortcut.
- **Weather** on the home screen, working without API keys and cached when offline.
- **Uninstall protection:** removing an app requires a 4-digit PIN.
- **Backup and restore** of settings, app order, banners and wallpapers; restore from any folder, USB drive or SD card.
- System **language** and **keyboard** settings, a **power menu** (screen off, reboot), **update checks** on GitHub with a full-screen changelog, and an interface in **9 languages**.

### Installation
1. Download the APK from **[Releases](https://github.com/azimoff7007/Leanbackonfire/releases/latest)**.
2. Install it with Downloader, Send Files to TV, a USB drive or `adb install`.
3. Press **Home** and choose Leanback Launcher.

New versions install over old ones and keep your settings.

### ADB permissions
Some features need permissions Android TV does not grant from the screen. The commands are listed above and also inside the launcher: **Settings → About → ADB permissions**, with a QR code.

</details>
