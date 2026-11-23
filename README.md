# LoyaltyBox – Customer Loyalty & Rewards Platform

**Every Box Has a Reward. Every Purchase Builds Loyalty.**

LoyaltyBox is a digital customer loyalty and rewards management platform designed for manufacturing businesses that sell physical products in boxes.

The platform enables customers to earn loyalty points by purchasing genuine products and redeeming unique codes printed inside product packaging. It also provides factory owners with a centralized dashboard to manage products, generate unique QR codes, monitor customer activity, manage rewards, and detect suspicious redemption attempts.

The primary goal is to help manufacturers build stronger customer relationships, encourage repeat purchases, and create a transparent, secure, and manageable rewards ecosystem.

---

## 1. Project Overview

Traditional loyalty programmes often rely on physical coupons, membership cards, or manual reward tracking. These methods can be difficult to manage and vulnerable to duplicate claims and fraudulent activities.

LoyaltyBox aims to solve these problems through a digital, QR-code-based reward system.

Each product box is assigned a unique, securely generated redemption code. Customers can scan the QR code and submit the concealed verification code to prove possession of the product. Once verified, the system credits the corresponding loyalty points to the customer's account.

Customers can accumulate points and exchange them for available rewards.

Factory administrators can manage the complete loyalty programme through an administrative dashboard.

### Key Objectives

- Encourage customer loyalty and repeat purchases.
- Provide a simple and convenient reward-earning experience.
- Verify genuine product ownership through unique redemption codes.
- Prevent duplicate code redemption and fraudulent activities.
- Provide factory owners with centralized reward management.
- Monitor customer engagement and reward programme performance.

---

## 2. How It Works

The platform follows a simple purchase-to-reward workflow.

1. **Product Creation:** The factory administrator registers products and defines their corresponding loyalty points.

2. **Code Generation:** The administrator generates unique QR codes and redemption tokens for product batches.

3. **Product Packaging:** Generated QR codes are printed and placed inside product packaging with a concealed verification mechanism.

4. **Customer Purchase:** A customer purchases a product from a retail store.

5. **QR Scanning:** The customer logs into LoyaltyBox and scans the QR code printed inside the packaging.

6. **Purchase Verification:** The backend validates the submitted token and checks whether it is genuine and has already been redeemed.

7. **Points Allocation:** If verification succeeds, the system credits the appropriate loyalty points to the customer's wallet.

8. **Reward Redemption:** Customers can use their accumulated points to claim available rewards.

9. **Factory Monitoring:** Administrators monitor code usage, customer engagement, reward transactions, and suspicious activities.

---

## 3. User Roles

LoyaltyBox is designed around two primary user roles.

### Customer

Customers can:

- Register and log in securely.
- Manage their personal profiles.
- Scan product QR codes.
- Verify product redemption codes.
- Earn loyalty points.
- View their available points balance.
- Access transaction history.
- Browse available rewards.
- Redeem rewards.
- Track reward redemption history.

### Factory Administrator

Factory administrators can:

- Access the administrative dashboard.
- Manage customer accounts.
- Create, update, and manage products.
- Configure product-wise loyalty points.
- Manage manufacturing batches.
- Generate unique QR codes in bulk.
- Download QR code sheets for printing.
- Monitor generated and redeemed codes.
- Manage available rewards and reward inventory.
- View customer point transactions.
- Monitor suspicious redemption activities.
- Analyse customer engagement and reward programme performance.

---

## 4. Core Features

### 4.1 Authentication and User Management

Secure registration and authentication with role-based access control.

### 4.2 Product Management

Administrators can create and manage products, product categories, product information, and loyalty point values.

### 4.3 Unique QR Code Generation

The platform generates cryptographically secure, unique redemption tokens associated with individual product packages.

Administrators can generate codes in batches and download printable QR code sheets.

### 4.4 Purchase Verification

Customers prove possession of a genuine product package by scanning its QR code and submitting the concealed redemption token.

The backend verifies:

- Whether the token exists.
- Whether the token is associated with an active product.
- Whether the token is valid.
- Whether the token has already been redeemed.
- Whether the customer is eligible to redeem it.

### 4.5 Fraud Prevention

LoyaltyBox incorporates security mechanisms to reduce fraudulent redemption attempts.

Planned security measures include:

- Cryptographically secure random token generation.
- One-time code redemption.
- Hashed token storage.
- Atomic database transactions.
- Database-level uniqueness constraints.
- Rate limiting against repeated invalid attempts.
- Protection against simultaneous duplicate redemption.
- Suspicious activity monitoring.

### 4.6 Customer Wallet and Loyalty Points

Every customer has a digital wallet that maintains their loyalty points balance.

All point credits and deductions are recorded in a transaction ledger to maintain transparency and enable auditing.

### 4.7 Rewards Management

Administrators can create rewards, configure point requirements, manage availability, and maintain reward inventory.

Customers can browse and redeem rewards using their accumulated points.

### 4.8 Analytics and Monitoring

The administrative dashboard provides insights into:

- Total registered customers.
- Total generated QR codes.
- Total redeemed codes.
- Active customers.
- Points distributed.
- Points redeemed.
- Reward redemption activity.
- Popular products.
- Suspicious activities.

---

## 5. Technology Stack

The project will use a full-stack architecture with Django REST Framework as the backend API.

| Layer | Technology |
|---|---|
| Frontend | React.js |
| UI Styling | Tailwind CSS |
| Backend | Python, Django |
| REST API | Django REST Framework |
| Database | PostgreSQL |
| Authentication | JWT |
| QR Code Generation | Python `qrcode` |
| QR Code Scanning | `html5-qrcode` |
| API Testing | Postman |
| Automated Testing | Django TestCase / pytest |
| Data Visualization | Recharts |
| Version Control | Git and GitHub |
| Deployment | Vercel + Render or equivalent hosting |

### Why Django REST Framework?

Django REST Framework is selected because the application requires structured database management, authentication, role-based permissions, transactional operations, and multiple interconnected business modules.

Django provides:

- A powerful ORM for managing relational data.
- Built-in authentication and permission mechanisms.
- Database transaction support.
- Django Admin for administrative operations.
- A mature ecosystem of security and development tools.

DRF provides a structured approach to developing REST APIs that can communicate with the React frontend.

This combination allows the project to maintain a clean separation between frontend presentation and backend business logic.

---

## 6. System Architecture

LoyaltyBox follows a client-server architecture.

```text
             CUSTOMER / ADMIN
                    |
                    v
             REACT FRONTEND
                    |
              REST API / HTTPS
                    |
                    v
          DJANGO REST FRAMEWORK
                    |
          -----------------------
          |          |          |
          v          v          v
      Accounts    Products    Rewards
          |          |          |
          v          v          v
       Customer   QR Codes   Redemption
        Wallet    Verification  Engine
          |          |          |
          -----------|----------
                     |
                     v
                POSTGRESQL
                     |
                     v
            ANALYTICS & REPORTS
```

The React frontend communicates with the Django REST Framework backend through REST APIs.

Django handles authentication, business logic, QR code validation, reward calculations, and transaction management.

PostgreSQL stores customer information, products, generated codes, wallets, point transactions, and reward redemption records.

---

## 7. Database Design

The initial database design includes the following entities:

| Entity | Description |
|---|---|
| User | Stores customer and administrator accounts. |
| Product | Stores factory product information. |
| ProductBatch | Stores manufacturing batch details. |
| RewardCode | Stores unique product redemption code records. |
| Wallet | Maintains customer loyalty point balances. |
| PointTransaction | Records all loyalty point credits and deductions. |
| Reward | Stores available rewards and their point requirements. |
| RewardRedemption | Records customer reward redemption requests. |

The database structure will be refined during implementation to maintain data integrity, secure transactions, and scalability.

---

## 8. Security Considerations

Security is a fundamental part of LoyaltyBox because the platform directly manages reward credits and customer benefits.

The following measures will be considered during implementation:

- Secure password hashing.
- JWT-based authentication.
- Role-based API permissions.
- HTTPS for communication.
- Secure random redemption token generation.
- Hashed storage of redemption tokens.
- Atomic code redemption and wallet updates.
- Rate limiting.
- Input validation.
- Protection against duplicate redemption.
- Administrative activity monitoring.
- Environment-based configuration for sensitive credentials.

A successful redemption must update the redemption status and customer points within a single database transaction.

This ensures that a single product code cannot generate multiple reward credits through concurrent requests.

---

## 9. Project Structure

The planned repository structure is:

```text
LoyaltyBox/
│
├── backend/
│   ├── config/
│   ├── accounts/
│   ├── products/
│   ├── codes/
│   ├── wallet/
│   ├── rewards/
│   ├── analytics/
│   ├── requirements.txt
│   └── manage.py
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── layouts/
│   │   ├── services/
│   │   ├── hooks/
│   │   └── assets/
│   └── package.json
│
├── docs/
│
├── README.md
├── ASSUMPTIONS.md
├── ARCHITECTURE.md
├── AI_LOG.md
├── .env.example
└── .gitignore
```

The structure may evolve as additional modules are implemented.

---

## 10. Installation and Setup

### Prerequisites

Install the following before setting up the project:

- Python 3.11 or later.
- Node.js and npm.
- PostgreSQL.
- Git.

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/LoyaltyBox.git

cd LoyaltyBox
```

### Step 2: Backend Setup

Navigate to the backend directory.

```bash
cd backend
```

Create and activate a virtual environment.

**Windows:**

```bash
python -m venv venv

venv\Scripts\activate
```

**Linux / macOS:**

```bash
python3 -m venv venv

source venv/bin/activate
```

Install dependencies.

```bash
pip install -r requirements.txt
```

### Step 3: Environment Configuration

Create a `.env` file inside the backend directory using `.env.example` as a reference.

Configure the required database and application settings.

Example:

```env
DEBUG=True
SECRET_KEY=your-development-secret-key
ALLOWED_HOSTS=localhost,127.0.0.1

DB_NAME=loyaltybox_db
DB_USER=postgres
DB_PASSWORD=your-local-password
DB_HOST=localhost
DB_PORT=5432
```

Never commit actual passwords, secret keys, or production credentials.

### Step 4: Database Setup

Create a PostgreSQL database named `loyaltybox_db`.

Then run:

```bash
python manage.py makemigrations

python manage.py migrate
```

### Step 5: Create Administrator Account

```bash
python manage.py createsuperuser
```

Follow the instructions to create an administrator account.

### Step 6: Start the Backend Server

```bash
python manage.py runserver
```

Backend development server:

```text
http://127.0.0.1:8000/
```

### Step 7: Frontend Setup

Open another terminal and navigate to the frontend directory.

```bash
cd frontend

npm install

npm run dev
```

The React development server will provide its local URL, typically:

```text
http://localhost:5173/
```

---

## 11. Testing

Testing is important to ensure that loyalty points are credited correctly and product codes cannot be reused.

The project will include automated tests and manual verification for the following scenarios:

| Test Scenario | Expected Result |
|---|---|
| Valid QR code redemption | Points credited successfully |
| Duplicate code redemption | Redemption rejected |
| Invalid redemption token | Validation error displayed |
| Simultaneous redemption attempts | Only one request succeeds |
| Insufficient loyalty points | Reward redemption rejected |
| Unavailable reward | Redemption rejected |
| Unauthorized admin access | Access denied |
| Wallet balance verification | Balance matches transaction ledger |
| Repeated invalid attempts | Rate limit enforced |

Test results and any identified issues will be documented in the repository.

---

## 12. Project Documentation

The repository will maintain the following documentation:

| File | Purpose |
|---|---|
| README.md | Project overview, technology stack, setup, and usage instructions. |
| ASSUMPTIONS.md | Documents all assumptions made due to incomplete client requirements. |
| ARCHITECTURE.md | Explains technology decisions, system architecture, database design, and workflows. |
| AI_LOG.md | Documents important AI prompts, interactions, mistakes, and corrections. |
| .env.example | Provides placeholder environment configuration without exposing secrets. |

---

## 13. Future Enhancements

The following features may be considered after completing the initial version:

- Advanced fraud detection and anomaly analysis.
- Customer engagement analytics.
- Product-wise and region-wise loyalty reports.
- Multiple factory and brand support.
- Automated reward notifications.
- Referral-based loyalty programmes.
- Expiring loyalty points.
- Multilingual customer interface.
- Integration with external e-commerce platforms.
- Progressive Web App installation support.

These enhancements are outside the initial MVP unless explicitly included in the final project scope.

---

## 14. Project Status

**Development Status:** Planning / Initial Development

The project will be developed incrementally, with a focus on secure product verification, reliable loyalty point management, and an intuitive customer experience.

Features will be marked as completed only after implementation and testing.

---

## 15. Author

**Project:** LoyaltyBox – Customer Loyalty & Rewards Platform

**Repository:** [GitHub Repository](https://github.com/YOUR_USERNAME/LoyaltyBox)

**Developer:** Vyankatesh Gupta

---

*LoyaltyBox – Turning Every Genuine Purchase into a Rewarding Experience.*
