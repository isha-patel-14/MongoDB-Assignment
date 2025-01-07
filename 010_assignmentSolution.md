# 6. More Practice Task
## Task 1: Add multiple students
Insert at least 5 students into the students collection with unique roll numbers, names, departments, years, and subjects enrolled.
```
db.students.insertMany ([
{ name: "Aarav Patel", 
roll_number: 201, 
department: "Computer Science", 
year: 2, 
courses_enrolled: ["React", "NodeJS"] },

{ name: "Sanya Kapoor", 
roll_number: 202, 
department: "Electronics", 
year: 1, 
courses_enrolled: ["Digital Circuits", "NodeJS"] },

{ name: "Jenil Desai", 
roll_number: 203, 
department: "Information Technology", 
year: 3,
courses_enrolled: ["React", "MongoDB"] },

{ name: "Isha Sharma", 
roll_number: 204, 
department: "Mechanical", 
year: 4, 
courses_enrolled: ["Thermodynamics", "Mechanics"] },

{ name: "Rajiv Nair", 
roll_number: 205, 
department: "Computer Science", 
year: 2, 
courses_enrolled: ["NodeJS", "React"] }
]);
```

<br></br>

## Task 2: Add multiple subjects
Insert 4 subjects into the subjects collection, each with 3 to 5 topics.
```
db.subjects.insertMany ([
{ subject: "React", 
topics: ["Components", "State", "Props", "Hooks"] },

{ subject: "NodeJS", 
topics: ["Express", "Modules", "Middleware"] },

{ subject: "MongoDB", 
topics: ["Schema Design", "CRUD", "Aggregation"] },

{ subject: "React Native", 
topics: ["Components", "Navigation", "APIs"] }
]);
```

<br></br>

## Task 3: Query students based on subject enrollment
Query the students collection to find all students who are enrolled in NodeJS.
```
db.students.find({ courses_enrolled: "NodeJS" }).pretty();
```

<br></br>

## Task 4: Add a new topic to a subject
Add a new topic to the NodeJS subject.
```
db.subjects.updateOne(
  { subject: "NodeJS" },
  { $push: { topics: "Streams" } }
);
```

<br></br>

## Task 5: Query Subjects with Multiple Topics
Query the subjects collection to find subjects that contain at least 4 topics.
```
db.subjects.find({ topics: { $size: { $gte: 4 } } }).pretty();
```

<br></br>

## Task 6: Update student enrollment
Add the subject "React Native" to Jenil's subjects.
```
db.students.updateOne(
  { name: "Jenil Desai" },
  { $push: { courses_enrolled: "React Native" } }
);
```

<br></br>

## Task 7: Query all students
Query all students in the database and print out their names and enrolled subjects.
```
db.students.find({}, { name: 1, courses_enrolled: 1, _id: 0 }).pretty();
```

<br></br>

## Task 8: Update Multiple Students' Year
Update the year for all students in the Computer Science department to year 3.
```
db.students.updateMany(
  { department: "Computer Science" },
  { $set: { year: 3 } }
);
```

<br></br>

## Task 9: Add new topics to multiple subjects
Add new topics to React, NodeJS, and MongoDB subjects. Ensure each subject gets at least one new topic.
```
db.subjects.updateOne(
  { subject: "React" },
  { $push: { topics: "Context API" } }
);

db.subjects.updateOne(
  { subject: "NodeJS" },
  { $push: { topics: "Error Handling" } }
);

db.subjects.updateOne(
  { subject: "MongoDB" },
  { $push: { topics: "Indexing" } }
);
```

<br></br>

## Task 10: Remove a Topic from a Subject
Remove the topic "Express" from the NodeJS subject.
```
db.subjects.updateOne(
  { subject: "NodeJS" },
  { $pull: { topics: "Express" } }
);
```

<br></br>

## Task 11: Query All Students in a Specific Year
Query and return all students in year 2 or year 3.
```
db.students.find({ year: { $in: [2, 3] } }).pretty();
```

<br></br>

## Task 12: Delete a Student by Roll Number
Delete a student from the database using their roll number.
```
db.students.deleteOne({ roll_number: 203 });
```

<br></br>

## Task 13: Delete all students from a department
Delete all students who belong to the Electrical Engineering department.
```
db.students.deleteMany({ department: "Electrical Engineering" });
```

<br></br>

## Task 14: Retrieve all topics for a subject
Query the MongoDB subject and retrieve all topics listed for it.
```
db.subjects.findOne({ subject: "MongoDB" }, { topics: 1, _id: 0 });
```

<br></br>

## Task 15: Count the number of subjects in which a student is enrolled
Write a query that returns the number of subjects each student is enrolled in.
```
db.students.aggregate([
  {
    $project: {
      name: 1,
      courses_enrolled_count: { $size: "$courses_enrolled" }
    }
  }
]).pretty();
```