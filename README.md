Vehicle Registration Project

Overview
The **Vehicle Registration** project is a MuleSoft integration app that simulates how vehicle registration data can be collected, processed, and stored.  

It demonstrates:
- HTTP Listener to accept API requests
- DataWeave transformations (JSON ↔ XML)
- Database/MySQL integration
- RAML API Specification
- CloudHub deployment
- API security using Client ID & Secret

---

Features
- Accept vehicle registration details through a REST API
- Transform incoming data formats (JSON ↔ XML)
- Store registration records in a MySQL database
- Secure the API with **Client ID Enforcement**
- Deploy and test on **CloudHub** using Postman
- Manage API with RAML specification in Design Center

---

Project Structure

Vehicle-Registration/
│
├── src/main/mule/ # Mule flows
│ ├── vehicle-registration.xml
│ └── db-config.xml
│
├── src/main/resources/ # Properties and configs
│ ├── mule-app.properties
│ └── log4j2.xml
│
├── api/ # RAML specification
│ ├── vehicle-registration.raml
│ └── examples/
│ └── register-request.json
│
├── pom.xml # Project dependencies
└── README.md # Project documentation



---

API Specification (RAML)
The API is defined in **RAML (RESTful API Modeling Language)** and published to Exchange.  

Key Endpoints:
- `POST /register` → Register a new vehicle  
- `GET /vehicles` → Retrieve all registered vehicles  
- `GET /vehicles/{id}` → Retrieve vehicle by ID  

RAML file: [`api/vehicle-registration.raml`](api/vehicle-registration.raml)

---

Database Schema
The project uses MySQL with the following schema:

```sql
CREATE TABLE vehicle_registration (
    id INT PRIMARY KEY AUTO_INCREMENT,
    owner_name VARCHAR(100),
    plate_number VARCHAR(20),
    model VARCHAR(100),
    year INT,
    registered_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

