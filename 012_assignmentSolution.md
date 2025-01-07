# **MongoDB Tasks**
## Task 1: Add more students to the students collection
Add at least 5 new students to the students collection with unique names, roll numbers, and course enrollments.
```
db.students.insertMany([
{ 
    "name": "Riya",
    "rollNumber": 104,
    "department": "Information Technology",
    "year": 1,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Kabir",
    "rollNumber": 105,
    "department": "Mechanical Engineering",
    "year": 3,
    "coursesEnrolled": ["EE101", "EE102"]
  },
  { 
    "name": "Ananya",
    "rollNumber": 106,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Ishaan",
    "rollNumber": 107,
    "department": "Electrical Engineering",
    "year": 4,
    "coursesEnrolled": ["EE102"]
  },
  { 
    "name": "Neha",
    "rollNumber": 108,
    "department": "Civil Engineering",
    "year": 1,
    "coursesEnrolled": ["CS101"]
  }
]);
```

## Task 2: Insert a new course into the courses collection
Add a new course with the following details:
<li>Course Code: CS202</li>
<li>Name: Data Structures</li>
<li>Credits: 3</li>
<li>Instructor: Prof. Krishna</li>

```
db.courses.insertOne({
  "courseCode": "CS202",
  "courseName": "Data Structures",
  "credits": 3,
  "instructor": "Prof. Krishna"
});
```

## Task 3: Fetch a specific student's record by roll number
Use find() to fetch a student's information using their roll number (104).
```
db.students.find({"rollNumber":104});
```

## Task 4: Query all students who are enrolled in a particular course
Retrieve all students who are enrolled in "EE102".
```
db.students.find({ "coursesEnrolled": "EE102" });
```

## Task 5: Update a student's courses
Update the student with roll number 106 to enroll in an additional course "CS202".
```
db.students.updateOne(
  { "rollNumber": 106 },
  { $push: { "coursesEnrolled": "CS202" } }
);
```

## Task 6: Remove a course from a student's courses list
Remove the course CS101 from the student Mahir's list of enrolled courses.
```
db.students.updateOne(
  { "name": "Mahir" },
  { $pull: { "coursesEnrolled": "CS101" } }
);
```

## Task 7: Find all courses with 3 credits
Query the courses collection to find all courses where the credits field equals 3.
```
db.courses.find({ "credits": 3 });
```

## Task 8: Find students who have enrolled in more than 2 courses
Use $size operator to query students who are enrolled in more than 2 courses.
```
db.students.find({
  $expr: { $gt: [{ $size: "$coursesEnrolled" }, 2] }
});
```

## Task 9: Use the $in operator to find students enrolled in multiple courses
Use the $in operator to find students who are enrolled in either CS101 or EE101.
```
db.students.find({
  "coursesEnrolled": { $in: ["CS101", "EE101"] }
});
```

## Task 10: Fetch all students from a specific department (e.g., CSE)
Use a query to find all students in the Computer Science department.
```
db.students.find({
  "department": "Computer Science"
});
```

## Task 11: Query students who are in their 3rd year
Retrieve students who are in the 3rd year using the year field.
```
db.students.find({
"year":3
});
```

## Task 12: Query students using a range for their year
Find all students who are in 2nd or 3rd year by using the $gte operator.
```
db.students.find({
  "year": { $gte: 2, $lte: 3 }
});
```

## Task 13: Count the total number of students in each department
Use the $group stage of aggregation to group students by department and count them.
```
db.students.aggregate([
  {
    $group: {
      _id: "$department", 
      count: { $sum: 1 }  
    }
  }
]);
```

## Task 14: Group courses by credits
Group courses by their credit value and count how many courses there are for each credit value.
```
db.courses.aggregate([
  {
    $group: {
      _id: "$credits",  
      count: { $sum: 1 } 
    }
  }
]);
```

## Task 15: Find the highest credit course
Query for the course with the highest number of credits using the $sort operator.
```
db.courses.find().sort({ "credits": -1 }).limit(1);
```

## 