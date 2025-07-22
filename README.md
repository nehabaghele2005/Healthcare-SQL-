🏥 Healthcare SQL Project This project explores and analyzes healthcare data using SQL. It simulates a hospital database system containing key entities like Patients, Doctors, Appointments, Billing, and Prescriptions. The project performs various SQL queries to generate insights on appointments, payments, doctor workloads, and prescription details.

🗂️ Database Structure The project uses a sample healthcare database with the following tables:

patients: Stores patient details

doctors: Stores doctor details and specialties

appointments: Contains appointment records between patients and doctors

billing: Records billing information for each appointment

prescriptions: Includes medication prescribed during appointments

🧪 Sample Queries & Use Cases 🔍 Basic Data Exploration sql Copy Edit SELECT * FROM patients; SELECT * FROM appointments; SELECT * FROM billing; SELECT * FROM doctors; SELECT * FROM prescriptions;

📄 Appointment and Prescription Details for a Specific Patient SELECT * FROM appointments WHERE patient_id = 1; SELECT * FROM prescriptions WHERE appointment_id = 1; SELECT * FROM billing WHERE appointment_id = 2;

🧾 Appointment Billing Summary SELECT a.appointment_id, p.first_name AS patient_first_name, p.last_name AS patient_last_name, d.first_name AS doctor_first_name, d.last_name AS doctor_last_name, b.amount, b.payment_date, b.status FROM appointments a JOIN patients p ON a.patient_id = p.patient_id JOIN doctors d ON a.doctor_id = d.doctor_id JOIN billing b ON a.appointment_id = b.appointment_id;

✅ Paid Billing Records SELECT * FROM billing WHERE status = "paid";

💰 Total Billing and Paid Amount SELECT (SELECT SUM(amount) FROM billing) AS total_billed, (SELECT SUM(amount) FROM billing WHERE status = 'paid') AS total_paid;

🧑‍⚕️ Doctor Appointment Statistics by Specialty SELECT d.specialty, COUNT(a.appointment_id) AS number_of_appointments FROM appointments a JOIN doctors d ON a.doctor_id = d.doctor_id GROUP BY d.specialty;

📊 Appointment Reasons Frequency SELECT reason, COUNT(*) AS count FROM appointments GROUP BY reason ORDER BY count DESC;

📅 Latest Appointment per Patient SELECT p.patient_id, p.first_name, p.last_name, MAX(a.appointment_date) AS latest_appointment FROM patients p JOIN appointments a ON p.patient_id = a.patient_id GROUP BY p.patient_id, p.first_name, p.last_name;

👨‍⚕️ Doctor Appointment Count SELECT d.doctor_id, d.first_name, d.last_name, COUNT(a.appointment_id) AS number_of_appointments FROM doctors d LEFT JOIN appointments a ON d.doctor_id = a.doctor_id GROUP BY d.doctor_id, d.first_name, d.last_name;

💊 Pending Prescription Details (Ordered by Dosage) sql Copy Edit SELECT pr.prescription_id, pr.medication, pr.dosage, pr.instructions FROM prescriptions pr JOIN appointments a ON pr.appointment_id = a.appointment_id JOIN billing b ON a.appointment_id = b.appointment_id WHERE b.status = 'pending' ORDER BY dosage DESC;

📌 Objective The purpose of this project is to:

Understand relational healthcare data

Write efficient SQL queries for data extraction and reporting

Generate business insights from raw tables

Practice data handling using joins, grouping, aggregation, filtering, and subqueries

🛠️ Technologies Used SQL

MySQL / PostgreSQL (compatible syntax)

DBMS tools like MySQL Workbench or pgAdmin

📎 How to Use Clone this repository

Import the provided SQL schema into your local database

Run the queries in your preferred SQL editor

📈 Future Scope Data visualization with Power BI / Tableau

Integration with a frontend for appointment booking

Advanced analytics (e.g., churn prediction or prescription trends)

📬 Feedback & Contributions Feel free to fork this project, suggest improvements, or raise issues. Contributions are always welcome!
