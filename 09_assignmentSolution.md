# Assignment: Building the "CodingGita Students" database
## **1. Create the Database and Collections :-**
### Step 1: creating a database
```
use codinggita
```

Step 2: create the "student" collection
```
db.createCollection("students");
```

Step 3: create the "courses" collection
```
db.createCollection("courses");
```

## **2. Insert Sample Data :-**
### Step 1: Insert sample data into the "students" collection
```
db.students.insertMany([
  { 
    "name": "Jenil",
    "rollNumber": 101,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS102"]
  },
  { 
    "name": "Mahir",
    "rollNumber": 102,
    "department": "Computer Science",
    "year": 2,
    "coursesEnrolled": ["CS101", "CS103"]
  },
  { 
    "name": "Arjun",
    "rollNumber": 103,
    "department": "Electrical Engineering",
    "year": 3,
    "coursesEnrolled": ["EE101", "EE102"]
  }
]);
```

### Step 2: Insert sample data into the "courses" collection
```
db.courses.insertMany([
  { 
    "courseCode": "CS101", 
    "courseName": "Introduction to Programming", 
    "credits": 3, 
    "instructor": "Prof. Sharma" 
  },
  { 
    "courseCode": "CS102", 
    "courseName": "Data Structures", 
    "credits": 3, 
    "instructor": "Prof. Gupta" 
  },
  { 
    "courseCode": "CS103", 
    "courseName": "Algorithms", 
    "credits": 3, 
    "instructor": "Prof. Kapoor" 
  },
  { 
    "courseCode": "EE101", 
    "courseName": "Basic Electrical Engineering", 
    "credits": 4, 
    "instructor": "Prof. Verma" 
  },
  { 
    "courseCode": "EE102", 
    "courseName": "Circuit Theory", 
    "credits": 4, 
    "instructor": "Prof. Yadav" 
  }
]);
```

## **3. Querying Data :-**
### Step 1: Query students based on department (Computer Science department)
```
db.students.find({ "department": "Computer Science" });
```
This query will return all students who belong to the Computer Science department.
<br></br>

### Step 2: Query students based on year (to find students who are in year 2)
```
db.students.find({ "year": 2 });
```
This query will return all students who are in the second year.
<br></br>

### Step 3: Query students by course enrollment (students who are enrolled in CS101)
```
db.students.find({ "coursesEnrolled": "CS101" });
```
This query will return all students who are enrolled in the CS101 course.
<br></br>

## **4. Updating Data :-**
### Step 1: Update a student’s courses
```
db.students.updateOne(
  { "name": "Arjun" },
  { $push: { "coursesEnrolled": "CS102" } }
);
```
This command will update Arjun’s document by pushing CS102 into his coursesEnrolled array.
<br></br>

### Step 2: Update a course instructor 
```
db.courses.updateOne(
  { "courseCode": "CS102" },
  { $set: { "instructor": "Prof. Mehta" } }
);
```
This query updates the instructor field for the course CS102 to Prof. Mehta.
<br></br>

## **5. Deleting Data :-**
### Step 1: Delete a student record
```
db.students.deleteOne({ "name": "Arjun" });
```
This will delete the document where the name field is Arjun.
<br></br>

### Step 2: Delete all students from a specific department
```
db.students.deleteMany({ "department": "Electrical Engineering" });
```
This will delete all students in the Electrical Engineering department.
<br></br>

# **6. Practice Assignments :-**
## Task 1: Create a "CodingGita Students" database
Create a new MongoDB database called CodingGita. Add two collections and insert sample data into both collections.

<li> students: Name, roll number, department, year, courses enrolled.</li>

<li>courses: Course code, name, credits, instructor.</li>

### Step 1: Create a MongoDB Database
```
use CodingGita
```

### Step 2: Create and Populate the students Collection
```
db.students.insertMany([
  {
    name: "Isha",
    roll_number: 101,
    department: "Computer Sci",
    year: 2,
    courses_enrolled: ["CS101", "CS102"]
  },
  {
    name: "Falak",
    roll_number: 102,
    department: "Electronics",
    year: 1,
    courses_enrolled: ["EC101"]
  },
  {
    name: "Hetav",
    roll_number: 103,
    department: "Mechanical",
    year: 3,
    courses_enrolled: ["ME101", "ME102", "ME103"]
  }
]);
```
### Step 3: Create and Populate the courses Collection
```
db.courses.insertMany([
  { course_code: "CS101", 
  name: "Introduction to CS", 
  credits: 4, 
  instructor: "Dr. Arjun Gupta" },

  { course_code: "CS102", 
  name: "Data Structures", 
  credits: 3, 
  instructor: "Prof. Neha Reddy" },

  { course_code: "EC101", 
  name: "Digital Circuits", 
  credits: 4, 
  instructor: "Dr. Mohan Kumar" },

  { course_code: "ME101", 
  name: "Thermodynamics", 
  credits: 4, 
  instructor: "Dr. Kavita Singh" },

  { course_code: "ME102", 
  name: "Mechanics", 
  credits: 3, 
  instructor: "Prof. Ravi Sinha" },

  { course_code: "ME103", 
  name: "Manufacturing Tech", 
  credits: 3, 
  instructor: "Dr. Pooja Nair" }
]);
```
<br></br>

## Task 2: Perform CRUD operations
<li>Add a few more students and courses to the database.</li>


<li>Query data based on:</li>

    
    Department (e.g., "Computer Science").
    Year (e.g., "2").
    Courses enrolled (e.g., "CS101").

<li>Update the courses for a specific student (e.g., adding a new course).</li>


<li>Delete a student or course from the database.</li>


<br></br>

### Step 1: Add More Students and Courses

### <ins>Add students</ins>
```
db.students.insertMany([
  {
    name: "Ishaan Malhotra",
    roll_number: 104,
    department: "Computer Sci",
    year: 3,
    courses_enrolled: ["CS101", "CS103"]
  },
  {
    name: "Nidhi Gupta",
    roll_number: 105,
    department: "Electronics",
    year: 2,
    courses_enrolled: ["EC102", "EC103"]
  }
]);
```

### <ins>Add courses</ins>
```
db.courses.insertMany([
  { course_code: "CS103", 
  name: "Operating Systems", 
  credits: 4, 
  instructor: "Dr. Ravi Kapoor" },

  { course_code: "EC102", 
  name: "Analog Circuits", 
  credits: 4, 
  instructor: "Dr. Sunita Jain" },

  { course_code: "EC103", 
  name: "Microprocessors", 
  credits: 3, 
  instructor: "Prof. Anand Tiwari" }
]);

```

### Step 2: Query Data
### 1. Query students by department (Computer Sci):
```
db.students.find({ department: "Computer Sci" }).pretty();
```

### 2. Query students by year (2):
```
db.students.find({ year: 2 }).pretty();
```

### 3. Query students enrolled in a specific course (CS101):
```
db.students.find({ courses_enrolled: "CS101" }).pretty();
```

<br></br>

### Step 3: Update Data
### 1. Insert a new course into the courses collection:
```
db.courses.insertOne({
  course_code: "CS104",
  name: "Artificial Intelligence",
  credits: 3,
  instructor: "Dr. Veena Roy"
});
```

### 2. Update the student's courses_enrolled field:
```
db.students.updateOne(
  { name: "Ananya Sharma" },
  { $push: { courses_enrolled: "CS104" } }
);
```

<br></br>

### Step 4: Delete Data
### 1. Delete a student (Rohan Mehta):
```
db.students.deleteOne({ name: "Rohan Mehta" });
```

### 2. Delete a course (ME103):
```
db.courses.deleteOne({ course_code: "ME103" });
```