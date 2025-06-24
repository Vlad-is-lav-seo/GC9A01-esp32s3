

🕰️ ESP32 Wi-Fi Analog Clock with GC9A01 and NTP Sync
Этот проект отображает аналоговые часы на круглой TFT-матрице GC9A01 с разрешением 240×240, подключенной к ESP32. Время синхронизируется с интернетом через NTP (pool.ntp.org), а сам циферблат отрисовывается по изображению из массива или может быть заменён на программную отрисовку.

🚀 Возможности
Подключение к Wi-Fi и автоматическая синхронизация времени через NTP

Отрисовка часов на фоне кастомного изображения (clock_face)

Мягкая отрисовка стрелок и секундных меток

Экономичное обновление экрана без мерцания

Простая настройка под любой часовой пояс

🛠 Оборудование
ESP32S3 WROOM 30pin Dev Board

GC9A01 240×240 TFT-дисплей (SPI)

Соединение по SPI (проверь настройки в User_Setup.h для TFT_eSPI)

📦 Зависимости
TFT_eSPI

WiFi

time

⚙️ Настройки
Wi-Fi:
cpp
const char* ssid = "YOUR_WIFI_NAME";
const char* password = "YOUR_PASSWORD";
Часовой пояс:
cpp
const long gmtOffset_sec = 3 * 3600;      // например, GMT+3 для Украины
const int daylightOffset_sec = 0;
🔧 Использование
Помести clock_face.h (с C-массивом изображения, 240×240, RGB565) в ту же директорию, где находится .ino-файл.

Подключи библиотеку TFT_eSPI и корректно настрой SPI-пины.

Вот настройки User_setup.h которые заработали у меня:

#define GC9A01_DRIVER

#define TFT_WIDTH  240

#define TFT_HEIGHT 240

#define TFT_CS   15     // Chip Select

#define TFT_DC   23    // Data/Command

#define TFT_RST  4    // Reset

#define TFT_MOSI 12    // SPI Data

#define TFT_SCLK 14    // SPI Clock

#define LOAD_GLCD

#define LOAD_FONT2

#define LOAD_FONT4

#define LOAD_FONT6

#define LOAD_FONT7

#define LOAD_FONT8

#define LOAD_GFXFF

#define SPI_FREQUENCY  27000000

#define USER_SETUP_ID 931

Скомпилируй и загрузи скетч на плату ESP32.

Включи — и наслаждайся синхронизированными аналоговыми часами на твоём дисплее!

📝 Примечание
Фоновое изображение должно быть 240×240 в формате RGB565.

![Демо GC9A01](https://diy32.xyz/img-content/GC9A01.jpg)
Примеры проектов на esp32 с сайта diy32.xyz
Сервис для создания с массива из картинки. (https://javl.github.io/image2cpp/)
