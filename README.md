# 🛒 ShopHub – Online Shopping Center

**ATI Kegalle | HND Information Technology**
**Student:** R.D.E Jayarathna | **ID:** KEG/IT/2324/F/8

---

## 📁 Project Structure

```
ShopHub/
├── server.js              ← Express server (entry point)
├── setup.js               ← Run once to create admin account
├── package.json
├── .env                   ← Database & JWT config
├── .gitignore
├── config/
│   └── db.js              ← MySQL connection pool
├── middleware/
│   └── authMiddleware.js  ← JWT auth guard
├── routes/
│   ├── auth.js            ← /api/auth  (login, register)
│   ├── products.js        ← /api/products (CRUD)
│   └── cart.js            ← /api/cart
├── public/                ← Frontend (served statically)
│   ├── index.html         ← Shop homepage
│   ├── login.html
│   ├── register.html
│   ├── cart.html
│   ├── admin.html         ← Admin dashboard
│   ├── css/style.css
│   └── js/
│       ├── api.js         ← Shared API helper
│       ├── main.js
│       ├── auth.js
│       ├── cart.js
│       └── admin.js
└── database/
    └── shopping_db.sql    ← Database schema + sample data
```

---

## ⚙️ Tech Stack

| Layer    | Technology |
|----------|-----------|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Backend  | Node.js + Express.js |
| Database | MySQL |
| Auth     | JWT (JSON Web Tokens) + bcrypt |
| IDE      | VS Code |

---

## 🚀 STEP-BY-STEP SETUP ON YOUR LAPTOP

### Prerequisites – Install these first

1. **Node.js** (v18+) → https://nodejs.org  (download LTS)
2. **MySQL** → https://dev.mysql.com/downloads/mysql/
3. **VS Code** → https://code.visualstudio.com
4. **Git** → https://git-scm.com/downloads

---

### STEP 1 – Copy the project to your laptop

Move the `ShopHub` folder to wherever you keep your projects, e.g.:
```
C:\Users\YourName\Projects\ShopHub       (Windows)
/Users/yourname/Projects/ShopHub         (Mac/Linux)
```

---

### STEP 2 – Set up the MySQL Database

1. Open **MySQL Workbench** (or the MySQL command line).
2. Connect to your local MySQL server.
3. Open the file `database/shopping_db.sql`.
4. Click **Run** (⚡ lightning bolt) to execute the script.
   - This creates the `shopping_db` database, all tables, and 12 sample products.

---

### STEP 3 – Configure the .env file

Open `.env` in VS Code and update the values:

```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_mysql_password   ← change this!
DB_NAME=shopping_db
JWT_SECRET=shophub_super_secret_jwt_key_2025
PORT=3000
```

> If your MySQL root password is empty, leave `DB_PASSWORD=` blank.

---

### STEP 4 – Install Node.js dependencies

Open a terminal in the `ShopHub` folder (VS Code → Terminal → New Terminal):

```bash
npm install
```

This installs Express, MySQL2, JWT, bcrypt, etc. (takes ~1 minute).

---

### STEP 5 – Create the Admin account

```bash
node setup.js
```

You should see:
```
  ✅  Admin user created / updated
      Email    : admin@shophub.com
      Password : admin123

  🚀  Setup complete! Run "npm run dev" to start.
```

---

### STEP 6 – Start the server

```bash
npm run dev
```

Then open your browser and go to:

```
http://localhost:3000
```

🎉 **ShopHub is running!**

---

## 🔑 Default Accounts

| Role     | Email                  | Password |
|----------|------------------------|----------|
| Admin    | admin@shophub.com      | admin123 |
| Customer | Register via /register |          |

**Admin features** (go to `/admin.html` or click Admin in navbar):
- Add / Edit / Delete products
- View all products with stock levels
- Dashboard stats

**Customer features:**
- Browse & search products
- Filter by category
- Add to cart, update quantities, checkout

---

## 🌐 API Endpoints

### Auth
| Method | Route               | Description          |
|--------|---------------------|----------------------|
| POST   | /api/auth/register  | Create account       |
| POST   | /api/auth/login     | Login (returns JWT)  |
| GET    | /api/auth/me        | Get current user     |

### Products
| Method | Route               | Description              |
|--------|---------------------|--------------------------|
| GET    | /api/products       | All products (+ filters) |
| GET    | /api/products/:id   | Single product           |
| POST   | /api/products       | Add product (admin)      |
| PUT    | /api/products/:id   | Update product (admin)   |
| DELETE | /api/products/:id   | Delete product (admin)   |

### Cart
| Method | Route        | Description         |
|--------|--------------|---------------------|
| GET    | /api/cart    | Get cart items      |
| POST   | /api/cart    | Add to cart         |
| PUT    | /api/cart/:id| Update quantity     |
| DELETE | /api/cart/:id| Remove item         |
| DELETE | /api/cart    | Clear entire cart   |

---

## 📤 HOW TO UPLOAD TO GITHUB

### STEP 1 – Create a GitHub account
Go to https://github.com and sign up (free).

### STEP 2 – Create a new repository
1. Click the **+** button → **New repository**
2. Name it: `shophub-shopping-website`
3. Set to **Public** or **Private**
4. Do NOT initialize with README (you already have files)
5. Click **Create repository**

### STEP 3 – Open terminal in your ShopHub folder

```bash
# Initialize git
git init

# Add all files (the .gitignore will skip node_modules and .env)
git add .

# First commit
git commit -m "Initial commit: ShopHub online shopping website"

# Connect to your GitHub repository
# (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/shophub-shopping-website.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### STEP 4 – Verify
Go to `https://github.com/YOUR_USERNAME/shophub-shopping-website`
You should see all your files there! ✅

### STEP 5 – Future updates
Whenever you make changes:
```bash
git add .
git commit -m "Describe what you changed"
git push
```

---

## ⚠️ Important Notes

- The `.env` file is in `.gitignore` — it will NOT be uploaded to GitHub (this is correct, it contains your password).
- The `node_modules/` folder is also excluded (it's large and can be reinstalled with `npm install`).
- When someone clones your repo, they run `npm install` then set up their own `.env`.

---

*ShopHub – Built for ATI Kegalle HND IT 2025*
