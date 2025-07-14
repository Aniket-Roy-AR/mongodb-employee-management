# 📘 MongoDB Employee Management System

A practical shell-based MongoDB project that simulates a real-world HR system to manage employees — view data, update records, perform aggregations, and export reports.

---

## 🔧 Tools Used

- MongoDB Shell (v5.0)
- CMD / Terminal
- MongoImport & MongoExport
- VS Code (for script management)

---

## 💡 Features

- 🔍 Filter by department, designation, or salary
- ✍️ Promote employees and apply salary hikes
- 📊 Generate reports (avg salary, highest paid, count)
- 📤 Export filtered records as CSV

---

## 🖼️ Screenshots

| View Queries | Aggregation |
|--------------|-------------|
| ![Find All](Find_All_Query.png) | ![Aggregation](Aggregation.png) |
| ![Find](Find_Query.png) | |

| Sort & Update | Export |
|----------------|--------|
| ![Sort](Sort_Query.png) | ![Export](Exporting.png) |
| ![Update](UpdateMany_Modify.png) | |

---

## 🚀 How to Use

1. Clone the repo  
2. Use `mongoimport` to load `emp_sal.csv`  
3. Run queries using the MongoDB shell  
4. Use `mongoexport` for CSV generation

```bash
mongoexport --uri="mongodb://localhost:27017" \
  --db=test --collection=sal --type=csv \
  --fields=EID,DEPT,DESI,SALARY \
  --query="{\"DEPT\":\"HR\"}" \
  --out="exports/hr_employees.csv"
