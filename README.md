# Odoo Development Notes

1. Use official Docker image for development purposes

https://hub.docker.com/_/odoo

# Docker Compose file

```
services:
  web:
    image: odoo:17.0
    depends_on:
      - db
    ports:
      - "8069:8069"
  db:
    image: postgres:15
    ports:
      - "5432:5432"  # 👈 Expose Postgres
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_USER=odoo

```

http://localhost:8069/web/login


### 🔹 Concept of Databases in Odoo

1. **Multi-Tenant Architecture**:

   * Odoo supports multiple databases on a single server.
   * Each **database** represents a **separate instance** of Odoo — usually for a different company, client, or environment (e.g., dev/test/prod).

2. **Data Isolation**:

   * All data (users, configurations, apps, records) are isolated within a specific database.
   * Users logged into one database cannot access data in another.

3. **Database Management Interface**:

   * As shown in your screenshot (`localhost:8069/web/database/manager`), Odoo provides a web interface to:

     * **Create** a new database
     * **Backup** a database
     * **Duplicate** a database
     * **Delete** a database
     * **Restore** from a backup
     * **Set the master password** to secure these operations

4. **Master Password**:

   * This is required for administrative actions like creating or deleting a database.
   * Helps prevent unauthorized access or tampering.

5. **Use Cases**:

   * Hosting Odoo for multiple clients (SaaS mode)
   * Testing changes on a staging environment
   * Providing trial databases for demo purposes

Would you like help setting up or managing these databases programmatically or through the Odoo command line?

### 🔹 Managing App Settings in Odoo

In Odoo, each app has a dedicated app settings page which **Administrators** can access or users with the proper access rights

![Screenshot 2025-05-06 at 3 00 48 PM](https://github.com/user-attachments/assets/ea22ce8f-5332-46d5-87f1-b58d076d8f14)
![Screenshot 2025-05-06 at 3 01 10 PM](https://github.com/user-attachments/assets/7176bdf0-e994-4f67-adf9-eb41ab9ca297)

### 🧩 Managing Apps in Odoo

#### 1. Install Apps

Go to Apps

Search for any app (e.g., CRM, Sales, Inventory)

Click Install

#### 2. Uninstall Apps

From the Apps menu, search for the installed app

Click on the app, then click Uninstall

### 🔹 Enable Developer Mode in Odoo

Go to **Settings → Scroll down → Click Activate Developer Mode**

This unlocks access to:

- Technical features

- Custom views

- Record rules and groups

![Screenshot 2025-05-06 at 3 10 25 PM](https://github.com/user-attachments/assets/b9a1e6b6-4186-46eb-a288-165001d76ae3)



# Reference

- https://www.cybrosys.com/odoo-development-tutorial/
