# 📊 DVD Rental Summary Report (WGU Pre-Assessment Project)

This project analyzes rental data from the Showtime DVD database to identify the most frequently rented films. It includes detailed and summary reporting using SQL, along with automation features like user-defined functions, triggers, and a stored procedure.

This was completed as part of the **Advanced Data Management** course at WGU.

---

## 🧠 Project Objective

The goal of this project is to generate a business report that:

- Shows rental details for each film (who rented what and when)
- Summarizes which films are most frequently rented
- Automates reporting and keeps the summary up to date using SQL triggers
- Prepares the system for weekly or biweekly refresh via a stored procedure

---

## 🛠️ Tools & Technologies

- PostgreSQL
- PL/pgSQL
- SQL Functions, Triggers, Stored Procedures
- pgAgent (for job scheduling)

---

## 📁 Project Structure

| File                        | Description                                               |
|----------------------------|-----------------------------------------------------------|
| `format_date.sql`          | User-defined function to format dates                    |
| `create_tables.sql`        | DDL for both detailed and summary report tables          |
| `populate_detailed.sql`    | Query to populate the detailed table                     |
| `update_trigger.sql`       | Trigger function + trigger to update the summary table   |
| `refresh_procedure.sql`    | Stored procedure to refresh and repopulate both tables   |

---

## 🧾 Key Features

### ✅ Detailed Table

Includes every DVD rental with:
- `rental_id`, `film_id`, `film_title`
- Formatted `rental_date` and `return_date` (e.g., *Jul 01, 2025*)

### ✅ Summary Table

Aggregates rental counts per film:
- `film_id`, `film_title`, and `total_rentals`

### ✅ User-Defined Function

```sql
CREATE OR REPLACE FUNCTION format_date(ts TIMESTAMP)
RETURNS TEXT AS $$
BEGIN
    RETURN TO_CHAR(ts, 'Mon DD, YYYY');
END;
$$ LANGUAGE plpgsql;
