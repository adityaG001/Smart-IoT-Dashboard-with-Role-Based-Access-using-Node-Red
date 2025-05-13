# 🔧 Node-RED:Smart IoT Dashboard with Role-Based Access

A secure and role-based user interface controller built using Node-RED, allowing access control for Admin, User, and Guest roles with SQLite-based authentication.

## 🚀 Features

- 🌐 User authentication with SQLite
- 🔒 Role-based access (Admin, User, Guest)
- 🧩 Dynamic UI control using Node-RED Dashboard
- 👋 Welcome navbar with logout functionality
- 🗃️ Prepared statements for secure login
- 🔄 Session storage and global context management


## 🛠️ Setup Instructions

1. Install [Node-RED](https://nodered.org/docs/getting-started/local)
2. Add required nodes:
   - `node-red-dashboard`
   - `node-red-node-sqlite`
3. Import `flows-compact.json` or 'flows-formatted.json' into your Node-RED editor
4. Place `database.db` under a `/database` folder
5. Upload `esp32code.ino` to your Arduino device
6. Run Node-RED and open the dashboard in the browser

## 💾 Database Schema

Use the following SQLite script to recreate your database:

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT NOT NULL UNIQUE,
    password TEXT NOT NULL,
    role TEXT CHECK(role IN ('admin', 'user', 'guest')) NOT NULL
);

-- Example data
INSERT INTO users (username, password, role) VALUES ('admin', 'admin', 'admin');
INSERT INTO users (username, password, role) VALUES ('user1', 'user1', 'user');
INSERT INTO users (username, password, role) VALUES ('guest1', 'guest1', 'guest');

##🔌 Connecting IoT Components (ESP32)
This project can interface with IoT hardware components like LEDs, sensors, and touch modules using the ESP32. Below is the wiring guide:

🟢 Connect the LED
Anode (long leg) → 330Ω resistor

Resistor other end → GPIO 2 on ESP32

Cathode (short leg) → GND

🌡️ Connect the BMP280 Sensor (I2C)
VCC → 3.3V on ESP32

GND → GND on ESP32

SCL → GPIO 22

SDA → GPIO 21

👁️ Connect the IR Sensor
VCC → 3.3V on ESP32

GND → GND on ESP32

OUT → GPIO 4

✋ Connect the Touch Sensor
VCC → 5V on ESP32

GND → GND on ESP32

I/O → GPIO 5

##✅ To-Do / Future Features
⏱️ Auto logout on inactivity

🔒 Password hashing

🧪 Unit testing for backend logic

📊 Data logging with timestamps


##📘 User Manual
For a detailed walkthrough, implementation screenshots, and explanation, refer to the "User-Manual.pdf" file included in the repo.

##📜 License
MIT License
You are free to use, modify, and distribute this project with attribution.
