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
