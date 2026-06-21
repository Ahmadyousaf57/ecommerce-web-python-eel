# 🛍️ ClothSphere E-Commerce & AI Chatbot System

An advanced, feature-rich E-Commerce desktop-web hybrid application built using **Python (Eel)**, **Vanilla Web Technologies (HTML/CSS/JS)**, and **SQL Server**. This platform seamlessly integrates standard e-commerce functionalities (shopping cart, product management, checkout) with an intelligent AI chatbot and real-time customer-to-admin communication.

---

## ✨ Key Features

### 🛒 E-Commerce Functionality
- **User Authentication**: Secure Login and Registration system with roles (`Admin`, `Customer`). Includes Captcha integration.
- **Product Management**: Complete CRUD (Create, Read, Update, Delete) operations for categories and products.
- **Search & Filtering**: Search products dynamically by name, category, or price.
- **Shopping Cart**: Add to cart, adjust quantities, and calculate totals with discounts and delivery charges in real-time.
- **Checkout & Orders**: Place orders with various payment methods (JazzCash, EasyPaisa, Debit Card, PayPal) and track order status.

### 🤖 AI Chatbot Assistant
- **DeepInfra Integration**: Uses the `mistralai/Mixtral-8x7B-Instruct-v0.1` model.
- **Smart Shopping Assistant**: Customers can ask the bot questions in real-time right from the web interface.
- **Standalone Chatbot**: Includes a separate `chatbot.py` script for command-line interactions.

### 💬 Live Customer-Admin Chat
- Real-time messaging system between Customers and Administrators.
- Notifications for unread messages.
- Persistent chat history stored in the database.

### 🛠️ Admin Dashboard
- **Manage Users**: View, search, update, and delete registered user accounts.
- **Manage Products**: Add new inventory, update existing product details, and manage categories.
- **Manage Orders**: View customer orders and update their statuses.

---

## 🏗️ Technology Stack

- **Backend**: Python (3.x), [Eel](https://github.com/python-eel/Eel) (for desktop-web hybrid app creation)
- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Database**: Microsoft SQL Server (`pyodbc` for connection)
- **AI/LLM API**: DeepInfra API

---

## 📂 Project Structure

```text
VERSION 1.1.6/
├── chatbot/
│   ├── chatbot.py           # Standalone CLI Python AI Chatbot script
│   └── .env                 # Environment variables for the standalone chatbot
├── web1/
│   ├── index.py             # MAIN APPLICATION ENTRY POINT (Backend + Server)
│   ├── Main.html            # Main UI Entry Point (Frontend)
│   ├── *.html               # Various UI views (Login, Cart, AdminPanel, etc.)
│   ├── *.js                 # Frontend logic (AddTOCart.js, AiChatbot.js, etc.)
│   ├── CSS/                 # Stylesheets
│   ├── IMAGES/              # Product and system images
│   ├── VIDEOS/              # Promotional/System videos
│   └── DATABASE/            # Database schema/scripts
└── README.md                # Project documentation
```

---

## 🛠️ Prerequisites

Before running this project, ensure you have the following installed:
1. **Python 3.x**
2. **Microsoft SQL Server** (running locally or remotely).
3. **DeepInfra API Key** (for the AI Chatbot functionality).

### Required Python Libraries:
```bash
pip install eel pyodbc requests python-dotenv
```

---

## ⚙️ Installation & Setup

### 1. Clone/Download the Repository
Extract the project files to your desired directory.

### 2. Database Configuration
1. Open SQL Server Management Studio (SSMS).
2. Create a database named `CLOTHS_ECOMMERCE_SITE1`.
3. Ensure you have the following tables created based on the application's schema:
   - `SIGN_UP`, `LOG_IN`, `Products`, `Categories`, `Cart`, `Orders`, `PaymentDetails`, `Messages`.
4. Open `web1/index.py` and modify the SQL connection string if your server name differs (Currently set to `DESKTOP-N8G6EHI\SQLEXPRESS`):
   ```python
   conn = pyodbc.connect(
       'DRIVER={SQL Server};'
       'Server=YOUR_SERVER_NAME;'
       'Database=CLOTHS_ECOMMERCE_SITE1;'
       'Trusted_Connection=yes;'
   )
   ```

### 3. Environment Variables (.env)
Create a `.env` file inside the `web1` directory and the `chatbot` directory:
```env
DEEPINFRA_API_KEY=your_deepinfra_api_key_here
```

---

## 🚀 How to Run the Application

### Running the Full E-Commerce Application
To launch the main e-commerce platform with the GUI:
1. Open a terminal/command prompt.
2. Navigate to the project root directory.
3. Execute the `index.py` file:
   ```bash
   python web1/index.py
   ```
   *(Note: The Eel library requires `web1` to be accessed correctly relative to where you run it. Running from the root is standard, as `index.py` initializes Eel with `eel.init('web1')`)*

### Running the Standalone Chatbot
If you simply want to test the AI model via terminal:
1. Navigate to the `chatbot` directory.
2. Run the script:
   ```bash
   cd chatbot
   python chatbot.py
   ```
3. Type your messages to chat with the AI, and type `quit` to exit.

---

## 🔐 Modules & Functionality Flow

- **Login/Signup Flow**: Uses SQL Server for fast queries. Profile pictures are encoded in Base64 for database storage. 
- **Product Fetching**: Javascript files (like `Displayproduct.js`) use `@eel.expose` decorators to request SQL data asynchronously without reloading the page.
- **Cart Management**: The cart maintains state based on the user's current `SessionID`, dynamically computing total prices minus discounts in the Python backend before sending it to the frontend.
- **AI Chatbot**: Handled via `AiChatbot.js` which talks to the `handle_chat_message` Python function, sending prompts to DeepInfra's Mixtral-8x7B endpoint.

---

<div align="center">
  <p><b>Built for the Theory of Programming Language Semester Project.</b></p>
  
  <br>
  
  <img width="1600" height="900" alt="Screenshot From 2026-06-21 15-16-56" src="https://github.com/user-attachments/assets/2256b8b9-442b-4934-84d4-5a4ee989a485" />
  <img width="1600" height="900" alt="Screenshot From 2026-06-21 15-15-21" src="https://github.com/user-attachments/assets/408d96b8-785c-473d-b415-de3c0dd799d0" />
</div>
