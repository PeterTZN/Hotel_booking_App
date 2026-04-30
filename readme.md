# 🏨 Hotel Booking App

A Python command-line application that allows users to browse available hotels, validate and authenticate credit card details, make hotel reservations, and optionally book spa packages — all powered by CSV data files and Object Oriented Programming.

---

## 📋 Table of Contents

- [About](#about)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Classes Overview](#classes-overview)
- [Future Improvements](#future-improvements)
- [License](#license)

---

## 📖 About

Hotel Booking App is a Python command-line tool that displays a list of available hotels, accepts user input to select a hotel, validates and authenticates credit card details against a database, generates a reservation ticket upon successful booking, and optionally books a spa package. Built using Object Oriented Programming principles including **inheritance** with CSV-based data storage.

---

## ✨ Features

- 🏨 Displays a list of hotels with availability status
- 🔍 Checks hotel availability before booking
- 💳 Validates credit card details against a card database
- 🔐 Two-factor style credit card **authentication** via password
- 🎫 Generates a reservation ticket upon successful booking
- 💆 Optional spa package booking with separate spa ticket
- 📂 Updates hotel availability in real time via CSV
- 🧩 Clean OOP design using **inheritance** between classes

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| Python 3 | Core programming language |
| `pandas` | Reading and updating CSV data files |

---

## 📁 Project Structure

```
Hotel_booking_App/
│
├── main.py               # Main application script
├── hotels.csv            # Hotel data (id, name, city, capacity, available)
├── cards.csv             # Valid credit card data for validation
├── card_security.csv     # Credit card passwords for authentication
├── requirements.txt      # Project dependencies
└── README.md             # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have Python 3 installed. Then install the required dependencies:

```bash
pip install pandas
```

Or install from `requirements.txt`:

```bash
pip install -r requirements.txt
```

### Clone the Repository

```bash
git clone https://github.com/PeterTZN/Hotel_booking_App.git
cd Hotel_booking_App
```

---

## ▶️ Usage

Run the script from the terminal:

```bash
python main.py
```

The app will:
1. 📋 Display all available hotels
2. ⌨️ Prompt you to enter a hotel ID
3. 🔍 Check if the hotel is available
4. 💳 Validate your credit card details
5. 🔐 Authenticate your credit card password
6. 🎫 Generate a reservation ticket if successful
7. 💆 Optionally book a spa package
8. 📂 Update hotel availability in `hotels.csv`

---

## ⚙️ How It Works

```
1. Load CSV files       → hotels.csv, cards.csv, card_security.csv
2. User selects hotel   → SpaHotel object created with selected ID
3. Check availability   → Confirms hotel is available to book
4. SecureCreditCard     → Card number passed to constructor
5. validate()           → Checks card details against cards.csv
6. authenticate()       → Checks password against card_security.csv
7. hotel.book()         → Updates availability to "no" in CSV
8. ReservationTicket    → Generates and prints booking confirmation
9. Spa option           → Optionally books spa and prints SpaTicket
```

---

## 🏗️ Classes Overview

### 🏨 `Hotel`
| Method | Description |
|--------|-------------|
| `__init__(hotel_id)` | Initialises hotel with ID and name |
| `available()` | Returns True if hotel is available |
| `book()` | Updates hotel availability to "no" in CSV |

### 🏊 `SpaHotel` *(inherits from Hotel)*
| Method | Description |
|--------|-------------|
| `book_spa_package()` | Books a spa package for the hotel |

### 💳 `CreditCard`
| Method | Description |
|--------|-------------|
| `__init__(number)` | Initialises card with card number |
| `validate(expiration, holder, cvc)` | Validates card details against cards.csv |

### 🔐 `SecureCreditCard` *(inherits from CreditCard)*
| Method | Description |
|--------|-------------|
| `authenticate(given_password)` | Authenticates card via password in card_security.csv |

### 🎫 `ReservationTicket`
| Method | Description |
|--------|-------------|
| `__init__(customer_name, hotel_object)` | Initialises ticket with name and hotel |
| `generate()` | Returns a formatted hotel booking confirmation |

### 💆 `SpaTicket`
| Method | Description |
|--------|-------------|
| `__init__(customer_name, hotel_object)` | Initialises ticket with name and hotel |
| `generate()` | Returns a formatted spa booking confirmation |

---

## 🔗 Inheritance Structure

```
Hotel
  └── SpaHotel

CreditCard
  └── SecureCreditCard
```

---

## 📄 Sample Output

```
   id                     name        city  capacity available
0  134  Tourist Sunny Apartment   Anchorage         4       yes
1  188              Snow Palace   New Delhi         5       yes
2  655           City Break Inn  Porto-Novo         3        no

Enter the id of the hotel: 188

        Thank you for your reservation!
        Here is your booking data:
        Name: John Smith
        Hotel name: Snow Palace

Do you want to book a spa package? yes

        Thank you for your spa reservation!
        Here is your booking data:
        Name: John Smith
        Hotel name: Snow Palace
```

---

## 🔮 Future Improvements

- [ ] Fully implement `book_spa_package()` method
- [ ] Add a graphical user interface (GUI)
- [ ] Add more detailed error handling
- [ ] Support multiple room bookings
- [ ] Add booking cancellation feature
- [ ] Move data storage from CSV to SQLite database
- [ ] Add user login and authentication

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

> Built with ❤️ using Python