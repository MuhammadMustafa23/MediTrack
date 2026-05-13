# MediTrack

A hospital management system for **The Ivor Paine Memorial Hospital**, built as a Database Lab project (Milestone 3). It provides a PHP web front end connected to a Microsoft SQL Server database, covering patient records, ward management, consultant teams, and 12 required analytical queries.

---

## Features

- **Dashboard** — live stats: total patients, doctors, wards, care units, treatments, and complaints; recent activity feed; disease summary chart; ward occupancy table
- **Patient Records** — view full medical details per patient including bed, care unit, consultant, doctor-in-charge, and treatment history
- **Ward Report** — wards with their day/night sisters, care units, and staff nurse in charge
- **Consultant Team** — consultants, their specialties, and the doctors in each team
- **Queries Page** — run all 12 project-required SQL Server reports directly from the browser with dynamic filters

---

## Tech Stack

| Layer    | Technology                              |
|----------|-----------------------------------------|
| Frontend | PHP 8, HTML/CSS, Vanilla JS             |
| Database | Microsoft SQL Server (SQLEXPRESS)       |
| Driver   | Microsoft Drivers for PHP (sqlsrv)      |
| Server   | Apache / IIS (XAMPP or IIS compatible)  |

---

## Database Schema

25 tables covering the full hospital domain:

- **Staff** — `Nurse`, `StaffNurse`, `DaySister`, `NightSister`, `NonRegisteredNurse`, `Position`, `NursePhone`, `NurseQualifications`, `DaySisterRound`
- **Doctors** — `Doctor`, `Consultant`, `DoctorTeamRecord`, `DoctorPhone`, `DoctorQualifications`, `PreviousExperience`, `PerformanceHistory`
- **Wards** — `Ward`, `Specialty`, `CareUnit`, `Bed`
- **Patients** — `Patient`, `PatientPhoneNumber`
- **Medical** — `Complaint`, `Treatment`, `TreatmentRecord`

---

## Project Structure

    hospital/
    ├── index.php                    # Dashboard
    ├── patientRecord.php            # Patient lookup
    ├── wardRecord.php               # Ward report
    ├── consultantTeam.php           # Consultant teams
    ├── queries.php                  # 12 SQL queries runner
    ├── config.php                   # DB connection config
    ├── includes/
    │   ├── database.php             # Query helpers & utilities
    │   ├── hospitalQueries.php      # All 12 query implementations
    │   ├── header.php
    │   └── footer.php
    └── assets/
        ├── style.css
        └── app.js

    sql/
    ├── ..._ddlScript.sql                 # Full schema (25 tables)
    ├── ..._initialInsertionCommands.sql  # Seed data
    └── ..._queries.sql                   # All 12 standalone queries

---

## Setup & Installation

### Prerequisites

- PHP 8.x with the `sqlsrv` and `pdo_sqlsrv` extensions enabled
- Microsoft SQL Server (Express edition works)
- Apache (XAMPP) or IIS
- [Microsoft Drivers for PHP for SQL Server](https://learn.microsoft.com/en-us/sql/connect/php/download-drivers-php-sql-server)

### Steps

1. **Clone the repository**

       git clone https://github.com/MuhammadMustafa23/MediTrack.git

2. **Create the database** — open SQL Server Management Studio (SSMS) and run:

       sql/..._ddlScript.sql
       sql/..._initialInsertionCommands.sql

3. **Configure the connection** — edit `hospital/config.php`:

       $serverName   = "localhost\\SQLEXPRESS";  // change if needed
       $databaseName = "IvorPaineHospital";

4. **Place in web root** — copy the `hospital/` folder into your Apache `htdocs` or IIS `wwwroot`.

5. **Open in browser**

       http://localhost/hospital/

---

## SQL Queries Included

| #   | Report |
|-----|--------|
| Q1  | Consultants and doctors in their team |
| Q2  | Wards with sisters, care units, and staff nurse in charge |
| Q3  | Patients with complaints, treatments, and dates |
| Q4  | Junior housemen, their patients, and care unit staff nurse |
| Q5  | Consultants with a unique specialty |
| Q6  | Complaints, treatments, and treating doctor's experience history |
| Q7  | Patients with more than one complaint and their treatments |
| Q8  | Patients grouped by treatment within complaint |
| Q9  | Performance history for a specific doctor *(filter by doctor)* |
| Q10 | Full medical details for a specific patient *(filter by patient)* |
| Q11 | Treatments for a complaint between two dates *(filter by complaint + date range)* |
| Q12 | Staff positions and count of staff in each position |

---
