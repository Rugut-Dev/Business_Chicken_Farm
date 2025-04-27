**Software Requirements Specification (SRS) Document**
---
# 1. Introduction
## 1.1 Purpose
This document outlines the Software Requirements Specification (SRS) for the Chicken Farm
Management System (CFMS), a software application designed to manage the daily operations
of a midsized poultry business focused on egg production. The system will assist in tracking
production units, flock records, feed consumption, egg production, sales, and customer
transactions.
## 1.2 Intended Audience
- Farm Owner
- Farm Manager
- Software Development Team
- QA Engineers
- Future Maintenance Teams
## 1.3 Scope
The CFMS will be a multi-platform application (Web and Mobile) that allows users to monitor
and manage the operations of a chicken farm with three distinct production units. Each unit will
operate independently within the system while contributing to the overall business reporting and
data aggregation.
## 1.4 Definitions and Abbreviations
- **CFMS**: Chicken Farm Management System
- **Production Unit**: A physical location or group of chicken coops managed separately
- **Flock**: A batch of birds added to a unit at a given time
- **Broken Eggs**: Eggs deemed unsuitable for sale due to damage
- **Feed**: The dietary input given to chickens
- **Egg Stock**: Number of saleable eggs after accounting for broken and sold eggs
---
# 2. Overall Description
## 2.1 Product Perspective
CFMS is a new, independent system tailored specifically for poultry farms with multiple
production units. It does not rely on or integrate with any existing software at this stage.
## 2.2 Product Functions
- Manage production units independently
- Track flocks per unit (arrival, breed, quantity, mortality, vaccinations)
- Manage feed inventory and consumption logs
- Record egg production per unit, per day
- Manage sales to individual customers
- Maintain customer records and sale history
- Generate operational reports
## 2.3 User Characteristics
- Users are primarily non-technical (farm staff and owners)
- Basic familiarity with mobile and desktop interfaces
## 2.4 Constraints
- All units must be managed separately
- Application must function well on mobile and web platforms
- Local Kenyan currency (KES) will be used
## 2.5 Assumptions and Dependencies
- The farm has consistent access to internet and electricity (assumption for web backend)
- Users will provide accurate data input
- Client may expand units in the future
---
# 3. Specific Requirements
## 3.1 Functional Requirements
### 3.1.1 Production Unit Management
- FR1.1: The system shall allow the Admin to create, edit, and delete production units.
- FR1.2: Each production unit shall be treated as an independent entity within the system.
### 3.1.2 Flock Management
- FR2.1: The system shall allow users to register a new flock with attributes (unit, breed, date of
arrival, quantity).
- FR2.2: The system shall allow users to update flock data including mortalities, vaccinations,
and health records.
- FR2.3: The system shall track the current number of live birds in each flock.
### 3.1.3 Feed Management
- FR3.1: The system shall allow feed purchase entries including supplier, quantity, and cost.
- FR3.2: Users shall be able to log daily feed consumption by production unit.
- FR3.3: The system shall calculate and display remaining feed stock.
### 3.1.4 Egg Production Management
- FR4.1: Users shall be able to record daily egg collection per unit.
- FR4.2: The system shall store number of eggs collected, broken eggs, and net saleable eggs.
- FR4.3: Egg stock shall be updated automatically upon entry of daily collection and sales.
### 3.1.5 Sales Management
- FR5.1: The system shall allow users to create sales records per customer.
- FR5.2: The user shall enter saleable egg quantity, price per egg, total amount, and customer
name.
- FR5.3: The system shall allow split sales — multiple customers can purchase from the same
day’s egg stock.
- FR5.4: The system shall deduct sold eggs from available stock.
### 3.1.6 Customer Management
- FR6.1: The system shall allow storage of customer details: name, phone, and purchase
history.
- FR6.2: Users can search and retrieve all past transactions for a given customer.
### 3.1.7 Reports Module
- FR7.1: The system shall generate production reports per unit and per time range (daily,
weekly, monthly).
- FR7.2: The system shall generate feed consumption and cost reports.
- FR7.3: The system shall generate sales reports including customer-wise and unit-wise
breakdown.
### 3.1.8 User Management
- FR8.1: The system shall have basic user roles: Admin, Manager, Worker.
- FR8.2: Each user role shall have defined access permissions (e.g., only Admin can delete
records).
- FR8.3: Users shall be authenticated using username and password.
## 3.2 Non-Functional Requirements
### 3.2.1 Performance
- NFR1: The system shall support up to 10 concurrent users without lag.
### 3.2.2 Usability
- NFR2: The system shall be intuitive and responsive, optimized for both mobile and desktop
views.
### 3.2.3 Availability
- NFR3: The system shall be available 99.9% of the time during farm working hours.
### 3.2.4 Security
- NFR4: All sensitive actions (edit, delete) shall require user authentication.
### 3.2.5 Maintainability
- NFR5: The backend shall be designed using a modular, scalable architecture.
---
# 4. Data Requirements
## 4.1 Database Entities
- Units (id, name, description)
- Flocks (id, unit_id, breed, arrival_date, quantity, mortality_count, vaccination_records)
- FeedInventory (id, unit_id, feed_type, quantity, purchase_date, cost)
- FeedLogs (id, unit_id, date, quantity_used)
- EggProduction (id, unit_id, date, total_eggs, broken_eggs)
- Sales (id, customer_id, unit_id, date, eggs_sold, unit_price, total_amount)
- Customers (id, name, phone)
- Users (id, name, role, password_hash)
## 4.2 Relationships
- Each flock belongs to one unit.
- Each egg production record is linked to one unit.
- Each sale is linked to one customer and one unit.
- Feed inventory and logs are unit-specific.
---
# 5. Appendices
## 5.1 Glossary
- **Batch**: Another term for a flock
- **Stock**: Refers to either feed inventory or unsold eggs
- **Unit**: Logical separation of farm structures
## 5.2 Future Enhancements (Optional for v2)
- SMS alerts for low feed
- Automated reports via email
- Integration with mobile money (e.g., M-Pesa)
---
