# 🏥 Elderly Care & Support Management System

*A Laravel-based donation and service management system for elderly care homes.*

---

## 📌 **Overview**

The **Elderly Care & Support System** is a full Laravel application built to manage day-to-day operations of an elderly home using donor funds.
It automates:

* Donation collection
* Fund allocation
* Weekly food management
* Resident service tracking
* Admin analytics
* Cost calculation
* Secure transactions
* Transparent reporting

The goal is to ensure that donations are used efficiently to support elderly residents with food, accommodation, hygiene, and events.

---

## 🧩 **Core Features**

### ⭐ 1. **Donation Management (Laravel + MySQL)**

* Accepts donations from authenticated users
* Stores donor details, amount, currency, transaction ID
* Tracks donation status
* Shows donation history on user profile
* Uses optimized Eloquent queries to calculate:

  * Total monthly donations
  * Top donors
  * Total revenue
  * Most donated day
  * Real-time donation analytics in admin panel

---

### ⭐ 2. **Food Menu & Cost Management (7-Day Repeat System)**

* Admin adds breakfast, lunch, dinner, and daily cost
* Prevents duplicate day entries using Laravel validation
* Displays weekly menu to users
* Calculates:

  * Total weekly food cost
  * Cost per resident
  * Monthly cost projections

---

### ⭐ 3. **Elderly Care Service Tracking**

Donations are mapped to services such as:

* Accommodation
* Food distribution
* Cleaning services
* Events & activities
* Healthcare support

Admin can update and manage all services from dashboard.

---

### ⭐ 4. **Admin Dashboard**

Built using Laravel Blade, Eloquent ORM & MySQL analytics.

Displays:

* Total donations
* This month’s revenue
* Top 10 donors
* Weekly food cost
* Most donated date
* Donation success / fail ratio
* Manage users
* Manage menu
* Manage donations
* Full CRUD for services, meals, and donors

---

## 🧠 **Important Laravel Queries Used**

### ✔ Fetch Monthly Revenue

```php
Donation::selectRaw('MONTH(created_at) as month, SUM(amount) as total')
    ->groupBy('month')
    ->get();
```

### ✔ Get Top Donors

```php
Donation::orderBy('amount', 'DESC')->take(5)->get();
```

### ✔ Check Duplicate Day in Food Table

```php
$exists = Food::where('day', $request->day)->exists();
```

### ✔ Total Food Cost

```php
$total = Food::sum('cost');
```

### ✔ Fetch Latest Donor Info

```php
Donation::with('user')->latest()->first();
```

### ✔ Donation Status Summary

```php
Donation::select('status', DB::raw('COUNT(*) as count'))
        ->groupBy('status')
        ->get();
```

---

## 🔐 **SSLCommerz Payment Gateway Integrated**

* Fully integrated Laravel payment API
* Handles hosted checkout
* Donation verification
* Callback URL support (success/cancel/fail)
* Stores full transaction logs

---

## 🛠 **Tech Stack**

| Technology         | Purpose               |
| ------------------ | --------------------- |
| **Laravel**        | Main framework (MVC)  |
| **PHP 8+**         | Backend engine        |
| **MySQL**          | Database & analytics  |
| **Blade**          | Templating engine     |
| **Bootstrap**      | UI design             |
| **Eloquent ORM**   | Database interactions |
| **SSLCommerz API** | Safe online donations |

---

## 📂 **Project Structure**

```
app/
    Http/
    Models/
    Controllers/
resources/
    views/
        admin/
        user/
routes/
    web.php
database/
    migrations/
public/
```

---

## 🚀 Installation

#### 1. Clone the repository

```
git clone https://github.com/yourusername/elderly-care-and-support
```

#### 2. Install dependencies

```
composer install
npm install && npm run dev
```

#### 3. Setup environment file

```
cp .env.example .env
```

Update database, SSLCommerz keys, APP_URL.

#### 4. Run migrations

```
php artisan migrate
```

#### 5. Start development server

```
php artisan serve
```

Access the app at:

```
http://localhost:8000
```

---

## 📈 **Future Enhancements**

* Mobile app (Flutter / React Native)
* AI-based food planning
* Donor analytics using charts
* Multi-language support
* Real-time notification system

---

## ❤️ **Purpose of the Project**

This system is developed to improve the management, transparency, and sustainability of elderly care homes.
It ensures every donation is **properly tracked, calculated, and utilized** to support the people who truly need it.

