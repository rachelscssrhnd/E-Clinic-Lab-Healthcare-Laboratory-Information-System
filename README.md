# E-Clinic Lab - Healthcare Laboratory Information System

**Final Project: Advanced Database | MySQL | Pentaho Data Integration | OLAP**

Designed and implemented a relational database system using MySQL to support transactional operations across healthcare laboratory branches.

Developed normalized database schemas and data models to ensure data consistency, integrity, and efficient query performance.

Architected an OLTP-OLAP environment by separating operational databases from analytical data warehouses to support reporting and decision-making.

Built end-to-end ETL pipelines using Pentaho Data Integration (PDI) to extract, transform, validate, and load data from transactional systems into the data warehouse.

Implemented data quality checks and transformation rules during ETL processes to improve data accuracy and reliability.

Developed analytical dashboards powered by the OLAP warehouse to monitor laboratory performance, operational trends, and branch-level metrics.

Optimized SQL queries and warehouse structures to improve reporting performance and support scalable analytical workloads.

---

## Tech Stack

- MySQL
- Pentaho Data Integration (PDI / Kettle)
- Laravel (PHP)
- Vite
- OLAP data warehouse

---

## Prerequisites

- PHP 8.x
- Composer
- Node.js and npm
- MySQL Server
- Pentaho Data Integration (optional, for running ETL jobs)

---

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/rachelscssrhnd/E-Clinic-Lab-Healthcare-Laboratory-Information-System.git
cd E-Clinic-Lab-Healthcare-Laboratory-Information-System
```

### 2. Install PHP Dependencies

```bash
composer install
```

### 3. Install Node Dependencies

```bash
npm install
```

### 4. Configure Environment Variables

```bash
cp .env.example .env
```

Open `.env` and update the database connection settings:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_database_name
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

### 5. Generate Application Key

```bash
php artisan key:generate
```

### 6. Import the Database

Two SQL files are provided:

- `basdat.sql` - OLTP transactional database (operational data)
- `dw_basdat.sql` - OLAP data warehouse (analytical data)

Import both into your MySQL server:

```bash
mysql -u your_username -p your_database_name < basdat.sql
mysql -u your_username -p your_dw_database_name < dw_basdat.sql
```

### 7. Run Database Migrations (if applicable)

```bash
php artisan migrate
```

### 8. Start the Development Server

In two separate terminals:

```bash
# Terminal 1: Laravel backend
php artisan serve
```

```bash
# Terminal 2: Vite frontend
npm run dev
```

The application will be available at:

```
http://localhost:8000
```

### 9. Running the ETL Pipeline

Open Pentaho Data Integration (Kettle) and load the transformation and job files located in the project. Run the jobs in the following order:

1. Run the extraction transformations to pull from the OLTP database
2. Run the transformation and validation steps
3. Run the load job to populate the data warehouse

---

## Project Structure

```
E-Clinic-Lab-Healthcare-Laboratory-Information-System/
├── app/            # Laravel application logic (models, controllers)
├── database/       # Migrations and seeders
├── public/         # Public assets
├── resources/      # Views and frontend resources
├── routes/         # Application routes
├── basdat.sql      # OLTP database dump
├── dw_basdat.sql   # OLAP data warehouse dump
├── .env.example    # Environment variable template
└── composer.json
```
