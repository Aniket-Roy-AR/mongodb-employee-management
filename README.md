# 💼 MongoDB Employee Management System
> A complete CRUD + Aggregation + Export project using MongoDB Shell

---

## 🔍 Project Summary

This project simulates a real-world employee management system using MongoDB shell.  
You can view, filter, update, aggregate, and export employee data using pure NoSQL commands.

🔧 Built with practical hands-on CLI operations  
📁 Based on a realistic HR dataset (`emp_sal.csv`)  
📊 Designed to demonstrate data analytics with MongoDB

---

## 📸 Screenshots Preview

| 🧾 Find Queries | 📊 Aggregation Queries |
|----------------|------------------------|
| ![Find All](screenshots/Find%20All%20Query.png) | ![Aggregation](screenshots/Aggregation.png) |
| ![Find Filtered](screenshots/Find%20Query.png) |                        |

| 🧮 Sort & Update | 📤 Exporting Data |
|------------------|------------------|
| ![Sort](screenshots/Sort%20Query.png) | ![Export](screenshots/Exporting.png) |
| ![UpdateMany](screenshots/UpdateMany%20Modify.png) | |

---

## 🔍 Core MongoDB Features Used

### 🧾 FIND & FILTER

```js
db.sal.find().pretty()
db.sal.find({ DEPT: "HR" }).pretty()
db.sal.find({ SALARY: { $gte: 50000, $lte: 100000 } }).pretty()

🔄 UPDATES
js
Copy
Edit
// Promote Executives
db.sal.updateMany({ DESI: "Executive" }, { $set: { DESI: "Sr. Executive" } })

// Raise IT salaries by 10%
db.sal.updateMany({ DEPT: "IT" }, { $mul: { SALARY: 1.10 } })
