# ASSUMPTIONS.md

# Bikaji Rewards — Project Assumptions

## 1. Project Overview

Bikaji Rewards is an academic software project that proposes a customer loyalty and rewards platform for Bikaji products.

The system allows customers to earn reward points by scanning unique QR codes placed inside eligible product packets. Customers can use their accumulated points to redeem available rewards.

The platform also provides a basic administration interface through which the factory owner or authorised administrator can manage products, QR codes, customers, points, and rewards.

**Project Note:** This is an academic prototype and is not affiliated with, officially sponsored by, or endorsed by Bikaji.

---

## 2. Business Assumptions

### A1. Initial Product Category

**Assumption:** The initial version will support only the Namkeen product category.

**Reason:** Starting with one product category keeps product management, QR generation, and reward calculations simple. Additional product categories can be introduced later.

### A2. Minimum Product MRP

**Assumption:** Only products with an MRP strictly greater than ₹150 are eligible for the loyalty programme.

**Reason:** This is the initial business rule selected for the project. Products priced at ₹150 or below will not generate reward points.

### A3. Product Eligibility

**Assumption:** The administrator will decide which products are eligible for the loyalty programme.

**Reason:** Not every product manufactured by the company needs to participate in the rewards programme.

### A4. Reward Points Configuration

**Assumption:** Each eligible product will have a predefined reward point value configured by the administrator.

**Reason:** Different products may have different MRPs and reward values. Keeping the point value configurable avoids hardcoding business rules.

### A5. QR Code Placement

**Assumption:** Every eligible product packet will contain one unique QR code placed inside the packaging.

**Reason:** Placing the QR code inside the packet makes it less accessible before the product is opened and discourages casual collection of unused codes.

### A6. One QR Code Per Product Packet

**Assumption:** Every eligible physical packet will have a different QR code, even when multiple packets belong to the same product and manufacturing batch.

**Reason:** A unique code allows the system to identify and track individual packet claims instead of treating all packets of a product as identical.

### A7. QR Code Reward Value

**Assumption:** The reward points associated with a QR code will be determined using the product's configured point value when the code is generated.

**Reason:** This ensures that previously generated codes retain their original reward value if an administrator changes the product's point configuration later.

### A8. Product Purchase Verification

**Assumption:** In the MVP, possession of a valid, unused QR code from an eligible packet will be accepted as sufficient evidence to claim reward points.

**Reason:** The QR code is placed inside the packet, making it a practical first-version method of encouraging genuine product purchases.

**Limitation:** This approach does not independently verify a retail transaction. Stronger purchase verification through retailer POS integration or receipt verification may be considered in future versions.

---

## 3. Customer Account Assumptions

### A9. Customer Registration

**Assumption:** Customers must create an account before claiming reward points.

**Reason:** A customer account is required to associate earned points with a specific person and maintain their reward history.

### A10. Mobile Number Verification

**Assumption:** Customers will register using their mobile number and verify it through OTP.

**Reason:** Mobile verification helps reduce duplicate and fake registrations.

### A11. One-Time Initial OTP Verification

**Assumption:** OTP verification will be required during initial customer registration. Existing verified customers will not need to verify their mobile number again every time they claim points.

**Reason:** This provides a simple customer experience without repeatedly requesting OTP verification.

### A12. Existing Customer Login

**Assumption:** Existing customers will log in to their accounts before claiming points if they are not already authenticated.

**Reason:** Customers should be able to access their accounts and accumulated points without creating a new account for every product.

### A13. One Account Per Mobile Number

**Assumption:** A verified mobile number can be associated with only one customer account.

**Reason:** This provides a basic mechanism for avoiding duplicate customer accounts.

---

## 4. QR Code and Redemption Assumptions

### A14. Unique QR Code Generation

**Assumption:** The system will generate a unique QR code for every eligible product packet.

**Reason:** Unique codes are necessary to track individual packet claims and prevent the same code from generating points repeatedly.

### A15. QR Code Scanning

**Assumption:** Scanning a QR code will open the Bikaji Rewards website and direct the customer to the claim process.

**Reason:** A web-based workflow allows customers to access the rewards programme without installing a separate mobile application.

### A16. New and Existing Customer Flow

**Assumption:**
- New customers will register and verify their mobile number before claiming points.
- Existing customers will log in and proceed directly to the claim process.
- Authenticated customers will be able to claim valid codes without repeatedly logging in.

**Reason:** This provides a consistent experience for both new and returning customers.

### A17. One-Time QR Redemption

**Assumption:** Each QR code can be successfully redeemed only once across the entire system.

**Reason:** The same packet must not generate reward points for multiple customers.

### A18. Invalid QR Codes

**Assumption:** The system will reject QR codes that do not exist, are invalid, or have already been redeemed.

**Reason:** Only valid and unused codes should generate reward points.

### A19. Automatic Point Allocation

**Assumption:** Reward points will be credited automatically after successful QR validation.

**Reason:** Automatic allocation reduces manual work and makes the claiming process convenient.

---

## 5. Loyalty and Reward Assumptions

### A20. Customer Wallet

**Assumption:** Every customer account will have a reward points balance.

**Reason:** A wallet provides a central place to track accumulated and spent points.

### A21. Point Transaction History

**Assumption:** The system will maintain a transaction history for earned and redeemed points.

**Reason:** Customers and administrators should be able to understand how the wallet balance was calculated.

### A22. Reward Redemption

**Assumption:** Customers will be able to redeem available rewards using their accumulated points.

**Reason:** Reward redemption gives customers a reason to participate in the loyalty programme.

### A23. Initial Reward Types

**Assumption:** The MVP will support a basic reward catalogue, such as:
- Free Bikaji products.
- Discount coupons.
- Gift hampers.

**Reason:** These reward types are easy to demonstrate without introducing complex third-party payment or delivery integrations.

### A24. Reward Point Cost

**Assumption:** Each reward will have a predefined point cost configured by the administrator.

**Reason:** The system needs a consistent way to determine whether a customer has enough points to redeem a reward.

### A25. Insufficient Points

**Assumption:** Customers cannot redeem rewards if their available point balance is lower than the required points.

**Reason:** This prevents customers from spending points they have not earned.

### A26. Reward Fulfilment

**Assumption:** In the MVP, reward fulfilment will be managed manually by the administrator.

**Reason:** Integrating external delivery services, coupon providers, or payment gateways would unnecessarily increase initial development complexity.

---

## 6. Factory Owner and Administration Assumptions

### A27. Administrator Access

**Assumption:** The system will provide a separate administrator interface for the factory owner or authorised staff.

**Reason:** Customer operations and business management require different permissions and interfaces.

### A28. Product Management

**Assumption:** Administrators can add, update, view, and deactivate eligible products.

**Reason:** Product information and eligibility rules may change over time.

### A29. QR Code Management

**Assumption:** Administrators can generate QR codes for eligible products and view their redemption status.

**Reason:** The factory needs to manage the codes associated with its products.

### A30. Customer Management

**Assumption:** Administrators can view registered customers and their reward point balances.

**Reason:** The factory needs basic visibility into customer participation.

### A31. Reward Management

**Assumption:** Administrators can add, update, and deactivate rewards and configure their point costs.

**Reason:** The reward catalogue should be manageable without changing application code.

### A32. Basic Dashboard

**Assumption:** The administrator dashboard will display basic operational statistics, including:
- Total registered customers.
- Total eligible products.
- Total QR codes generated.
- Total QR codes redeemed.
- Total points issued.
- Total rewards redeemed.

**Reason:** These statistics provide a simple overview of loyalty programme activity.

---

## 7. Technical Assumptions

### A33. Application Type

**Assumption:** Bikaji Rewards will be developed as a web application.

**Reason:** Customers can access the platform through a browser after scanning the QR code, without downloading a separate application.

### A34. Backend Technology

**Assumption:** Python, Django, and Django REST Framework will be used for backend development.

**Reason:** These technologies provide authentication, database management, API development, and administrative functionality while matching the development team's existing skills.

### A35. Frontend Technology

**Assumption:** React with Vite will be used to build the customer-facing and administrator interfaces.

**Reason:** React supports reusable UI components and provides a clear separation between frontend and backend development.

### A36. Database

**Assumption:** PostgreSQL will be used as the primary database.

**Reason:** The application requires reliable storage and relational relationships between customers, products, QR codes, point transactions, and rewards.

### A37. API Communication

**Assumption:** The React frontend and Django backend will communicate through REST APIs.

**Reason:** Separating the frontend and backend makes the application easier to maintain and test.

### A38. Responsive Interface

**Assumption:** The customer-facing website will support mobile devices, as most customers are expected to scan QR codes using smartphones.

**Reason:** A mobile-friendly interface is essential for a smooth QR-based customer experience.

### A39. QR Code Generation

**Assumption:** QR codes will be generated using a Python QR code generation library.

**Reason:** This provides a straightforward way to create unique QR images for eligible products.

### A40. OTP Delivery in the Prototype

**Assumption:** Actual SMS gateway integration may be simulated or mocked during initial development if a provider is not available.

**Reason:** The main objective of the initial prototype is to demonstrate registration and verification workflows without depending on paid external services.

---

## 8. MVP Scope and Limitations

The initial version will focus on the following functionality:

1. Customer registration and login.
2. Product and category management.
3. Manufacturing batch creation.
4. Unique QR code generation.
5. QR scanning and validation.
6. One-time QR redemption.
7. Automatic reward point allocation.
8. Customer wallet and transaction history.
9. Basic reward catalogue and redemption.
10. Administrator dashboard and management.

The following features are outside the initial MVP scope:

- Retailer POS integration.
- Receipt or invoice verification.
- Advanced fraud detection.
- AI-based customer analytics.
- Complex membership tiers.
- Referral programmes.
- Third-party payment gateway integration.
- Automated delivery and fulfilment integration.
- Advanced marketing campaign management.
- Automated factory packaging-line integration.
- Advanced device fingerprinting and fraud scoring.

These features may be considered after the basic system is functional and tested.

---

## 9. General Project Constraints

1. The initial implementation will prioritise simplicity, functionality, and maintainability.
2. All major business operations will be performed through the application rather than direct database manipulation.
3. Reward points must never be credited twice for the same QR code.
4. Customer point balances must remain consistent with their transaction history.
5. Administrative operations must be restricted to authorised users.
6. The system will use sample data for academic demonstration and testing.
7. Actual Bikaji production data, customer records, and manufacturing integrations are not assumed to be available.

---

## 10. Future Scope

After completing and testing the MVP, the following improvements may be considered:

- Stronger purchase verification through retailer POS integration.
- More advanced QR code activation and batch tracking.
- Improved fraud prevention and monitoring.
- Administrative audit logs.
- Bulk QR code export and packaging integration.
- Customer membership tiers.
- Promotional campaigns and bonus points.
- Advanced business analytics.
- Automated reward fulfilment.
- Scalable infrastructure for large production volumes.

---

## Conclusion

The assumptions documented in this file define the initial business rules, customer workflows, administrative responsibilities, and technical decisions for the Bikaji Rewards academic prototype.

These assumptions are intended to fill gaps in the assignment requirements and provide a clear foundation for development.

Any significant change to these assumptions during development should be documented and reflected in the project architecture and implementation.
