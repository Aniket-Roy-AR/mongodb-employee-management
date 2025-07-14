💼 MongoDB Employee Management System
📊 Complete NoSQL project using MongoDB Shell with CRUD, Aggregation & Export Operations

🔍 Overview
This project simulates a real-world Employee Management System using MongoDB Shell, showcasing core operations like:

🔎 View & filter employee records

✍️ Update roles and salaries

📊 Generate department-wise reports

📤 Export filtered data using mongoexport

Built for hands-on practice with real commands on a realistic dataset (emp_sal.csv).

📸 Screenshots
🔍 Find Queries	📊 Aggregations

🧮 Sort & Update	📤 Exporting

📁 Project Structure
java
Copy
Edit
mongodb-employee-management/
├── emp_sal.csv               ← Main dataset
├── queries/
│   ├── read_queries.js       ← db.find() operations
│   ├── update_queries.js     ← Promotions & salary updates
│   └── agg_queries.js        ← Aggregation pipelines
├── exports/                  ← CSV exports via mongoexport
│   └── hr_employees.csv
├── screenshots/              ← Terminal screenshot assets
└── README.md
🧪 Sample Commands
🔎 Find & Filter
js
Copy
Edit
db.sal.find().pretty()
db.sal.find({ DEPT: "HR" }).pretty()
db.sal.find({ SALARY: { $gte: 50000, $lte: 100000 } }).pretty()
🧾 Sorting
js
Copy
Edit
db.sal.find().sort({ SALARY: -1 }).pretty()
db.sal.find().sort({ DEPT: 1, SALARY: -1 }).pretty()
✍️ Update Records
js
Copy
Edit
// Promote Executives
db.sal.updateMany({ DESI: "Executive" }, { $set: { DESI: "Sr. Executive" } })

// Raise salary by 10% in IT
db.sal.updateMany({ DEPT: "IT" }, { $mul: { SALARY: 1.10 } })
📊 Aggregation Reports
js
Copy
Edit
// Avg salary per department
db.sal.aggregate([
  { $group: { _id: "$DEPT", avgSalary: { $avg: "$SALARY" } } }
])

// Top paid employee per dept
db.sal.aggregate([
  { $sort: { SALARY: -1 } },
  {
    $group: {
      _id: "$DEPT",
      topEID: { $first: "$EID" },
      topSALARY: { $first: "$SALARY" }
    }
  }
])
📤 Export Filtered Data
bash
Copy
Edit
mongoexport --uri="mongodb://localhost:27017" \
  --db=test --collection=sal --type=csv \
  --fields=EID,DEPT,DESI,SALARY \
  --query="{\"DEPT\":\"HR\"}" \
  --out="exports/hr_employees.csv"
