# Siyara Car Rental

Website of a car rental agency, built with Symfony. Project of the module
**Secure Application Development** (2026 / 2027).

A client searches for a car that is free on the dates they want, books it online and
follows the booking in a personal account. The administrators manage the cars, the
branches, the bookings, the clients and the reviews from a dashboard with statistics.

**Team:** Ghodhbane Ayoub, Benalaya Yousri

**Specifications (cahier des charges):**

- English: [docs/Ghodhbane_Benalaya_Project_Specifications_EN.pdf](docs/Ghodhbane_Benalaya_Project_Specifications_EN.pdf)
- Français : [docs/Ghodhbane_Benalaya_Cahier_des_charges_FR.pdf](docs/Ghodhbane_Benalaya_Cahier_des_charges_FR.pdf)

## Status

The repository holds the specifications. The Symfony project is added in phase 1.

## Features

Client side

- Register, log in, see and edit the account
- Catalogue of cars with search by dates, branch, category, gearbox, fuel, seats and price
- Booking in three steps: dates, summary with the total, confirmation
- List of the client's own bookings, with cancellation
- Reviews after a completed rental

Administration side

- Manage cars (with photo upload), categories and branches
- Manage bookings and clients
- Moderate reviews
- Statistics: bookings and revenue per month, bookings by status, most rented cars

## Security

| Threat | Measure |
| --- | --- |
| XSS | Twig auto-escaping, server-side validation, Content-Security-Policy |
| SQL injection | Doctrine ORM and QueryBuilder with bound parameters only |
| CSRF | CSRF token in every form and on every action that changes data |
| Broken access control | Roles, access rules and a Voter on the bookings |
| Weak authentication | Hashed passwords, password rule, login throttling |
| Dangerous upload | MIME type, extension and size checks, random file name |

## Stack

Symfony 6.4 LTS, PHP 8.1+, MySQL 8, Doctrine ORM, Twig, Bootstrap 5, EasyAdmin 4, Chart.js.

## Installation

To be used once the Symfony project is in the repository.

```bash
git clone https://github.com/Sliv3er/siyara-car-rental.git
cd siyara-car-rental
composer install
cp .env .env.local        # then set DATABASE_URL and APP_SECRET in .env.local
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
php bin/console doctrine:fixtures:load
```

## Git workflow

- `main` always holds a version that works.
- One branch per feature (`feature/car-crud`, `feature/booking`), merged into `main`
  with a pull request read by the other member.
- Each member commits with a personal GitHub account.
- `.env.local`, `vendor/`, `var/` and the uploaded photos are never committed.
