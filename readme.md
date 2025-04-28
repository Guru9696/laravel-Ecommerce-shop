
# Laravel Ecommerce Shop

Welcome to the Laravel Ecommerce Shop! This application offers a smooth and secure shopping experience with advanced features and integrated payment solutions. Below, you will find an overview of the technologies used, key features, and step-by-step instructions for setting up and running the application.

## Technologies

- **Laravel 11**: A powerful PHP framework that enables rapid development of robust web applications.
- **Livewire**: A dynamic framework for Laravel, simplifying the creation of interactive interfaces without leaving Laravel's ecosystem.
- **Tailwind CSS**: A utility-first CSS framework designed to quickly build modern, responsive user interfaces.
- **Stripe**: A secure and reliable payment processing platform, integrated with Laravel Cashier for seamless transactions.

## Features

- **Add to Cart as a Guest**: Visitors can add products to their shopping cart without needing to sign in.
- **Cart Persistence**: When a guest user logs into their account, the items in their cart are automatically merged with their account's cart.
- **Product Variants**: Customers can select different product options (like size or color) before adding them to their cart.
- **Stripe Payment Integration**: Secure payments via Stripe, facilitated through Laravel Cashier.
- **Abandoned Cart Email Reminders**: Automated daily email reminders are sent to users who have left items in their cart without completing the purchase.
- **Guest Cart Cleanup**: If a guest cart remains inactive for more than a day, it is automatically cleared.
- **Order History**: Users can view and manage their order history.
- **Order Confirmation Emails**: Automatic email confirmations are sent after a successful purchase.
- **Product Search Functionality**: Customers can easily search for products across the store.
- **Pagination for Products**: Large product lists are efficiently managed with pagination to enhance browsing performance.


## Setup Instructions

1. **Clone the repository:**
   ```bash
   git clone https://github.com/guru9696/laravel-Ecommerce-shop.git
   cd laravel-web-shop-app
   ```

2. **Install dependencies:**
   ```bash
   composer install
   npm install
   npm run dev
   ```

3. **Environment configuration:**
   Copy the `.env.example` file to `.env` and update the necessary environment variables, especially for database and Stripe API keys.
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Run migrations:**
   ```bash
   php artisan migrate
   ```

5. **Run the application:**
   ```bash
   php artisan serve
   ```

6. **Set up email notifications:**
   Ensure that your email settings are correctly configured in the `.env` file to enable email notifications for abandoned carts and order confirmations.

## Stripe Payment Gateway Local Setup

1. **Install Stripe CLI:**
   Download the Stripe CLI from the following link: [Stripe CLI](https://stripe.com/docs/stripe-cli)

2. **Listen to webhook events locally:**
   After installing the Stripe CLI, run the following command to listen to webhook events:
   ```bash
   stripe listen --forward-to YOUR_LOCAL_URL/stripe/webhook --format JSON
   ```

3. **Set up webhook secret:**
   Get the webhook signing secret from the Stripe dashboard and add it to the `.env` file as `STRIPE_WEBHOOK_SECRET`.
   ```bash
   STRIPE_WEBHOOK_SECRET=whsec_...
   ```

## Scheduled Commands

### Abandoned Cart Reminder

This feature sends an email reminder to users daily if they have items in their cart but haven't completed the purchase.

1. **Command:** `app/Console/Commands/AbandonedCart.php`
2. **Schedule:** The command is already scheduled in `routes/console.php` to run daily:
   ```php
   Schedule::command(AbandonedCart::class)->dailyAt('9:00');
   ```

### Remove Inactive Session Cart

This feature deletes guest carts that have been inactive for more than a day.

1. **Command:** `app/Console/Commands/RemoveInactiveSessionCart.php`
2. **Schedule:** The command is already scheduled in `routes/console.php` to run weekly:
   ```php
   Schedule::command(RemoveInactiveSessionCart::class)->weekly();
   ```

## Usage

Once the application is set up, you can start exploring the various features:

- Browse and search for products.
- Select different product variants and add them to the cart.
- Add products to the cart as a guest or logged-in user.
- Proceed to checkout using Stripe.
- Receive email notifications for abandoned carts and order confirmations mail.
- View your order history from the "My Orders" page.

## Contact
For any inquiries or support, please contact [Your Name] at [your-email@example.com].


