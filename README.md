# Schema-Design-Questions

## Question 1
# Movies Schema Design Project

This project is a sample implementation of a database schema for a movie database. The database contains information about movies such as the title, year of release, director, and actors.

## Tables and Attributes

The schema consists of the following tables and attributes:

### Movies

- **movie_id** (integer): Unique identifier for each movie
- **title** (string): Title of the movie
- **year** (integer): Year of the movie release
- **director_id** (integer): Foreign key to the Directors table

### Directors

- **director_id** (integer): Unique identifier for each director
- **name** (string): Name of the director

### Actors

- **actor_id** (integer): Unique identifier for each actor
- **name** (string): Name of the actor

### Movie_Actors

- **movie_id** (integer): Foreign key to the Movies table
- **actor_id** (integer): Foreign key to the Actors table

## Relationships

The relationships between the tables are as follows:

- A movie is directed by one and only one director, and a director can direct multiple movies. Therefore, the Movies table has a foreign key to the Directors table.
- An actor can star in multiple movies, and a movie can have multiple actors. Therefore, we have a many-to-many relationship between the Movies and Actors tables, which is implemented using a junction table called Movie_Actors.

## Database Design

The following diagram illustrates the database schema design:

![Movies Schema Design](movies_schema_design.png)

## Queries

The schema is normalized enough to avoid duplicating strings too much, and it can efficiently answer questions like the following:

- **Who acted in Fight Club (1999)?**

  To answer this question, we can join the Movies table with the Movie_Actors and Actors tables, and filter the results by the movie title and year.

- **What are the 10 most recent movies that George Clooney starred in?**

  To answer this question, we can join the Movies table with the Movie_Actors and Actors tables, and filter the results by the actor name. We can then sort the results by the movie year in descending order and limit the results to 10.

## Conclusion

This project provides a sample implementation of a database schema for a movie database. The schema is designed to efficiently store and query information about movies, directors, and actors. It can be extended and customized to suit specific needs and requirements.


## Question 2

Sure, here's the formatted text that you can copy and paste into your README.md file:

# Scaler Academy Schema Design Project

This project is a sample implementation of a database schema for an online learning platform called Scaler Academy. The database contains information about students, batches, lectures, assignments, homework, instructors, and more.

## System Requirements

The schema satisfies the following system requirements:

1. Students can register for different batches (e.g., Feb'20).
2. Students attend daily lectures on various topics (like Trees, Linked Lists, Stacks, etc.).
3. Every lecture has an assignment and homework.
4. Every assignment and homework can have 0-10 problems.
5. Every class has an instructor, some pre-lecture content, and lecture notes.
6. Students can see the class timeline, problem-solving percentage, attendance percentage, and status of all the problems in all the assignments/homework in the dashboard.
7. Instructors can see a list of classes taken by them and their upcoming classes.
8. Instructors can create lessons for all the batches and add/modify the assignments and homework problems.

## Future Scope

The schema can be extended to support the following features:

1. Store ratings and feedback for the class.
2. Collaborative lectures taken by multiple instructors.
3. Daily streak calculation.

## Tables and Attributes

The schema consists of the following tables and attributes:

### Students

- **student_id** (integer): Primary key for each student
- **name** (string): Name of the student
- **email** (string): Email address of the student

### Batches

- **batch_id** (integer): Primary key for each batch
- **name** (string): Name of the batch (e.g., Feb'20)

### Lectures

- **lecture_id** (integer): Primary key for each lecture
- **batch_id** (integer): Foreign key to the Batches table
- **topic** (string): Topic of the lecture (e.g., Trees, Linked Lists, Stacks)
- **instructor_id** (integer): Foreign key to the Instructors table
- **prelecture_content** (text): Pre-lecture content for the lecture
- **lecture_notes** (text): Notes for the lecture

### Assignments

- **assignment_id** (integer): Primary key for each assignment
- **lecture_id** (integer): Foreign key to the Lectures table
- **name** (string): Name of the assignment
- **num_problems** (integer): Number of problems in the assignment

### Homework

- **homework_id** (integer): Primary key for each homework
- **lecture_id** (integer): Foreign key to the Lectures table
- **name** (string): Name of the homework
- **num_problems** (integer): Number of problems in the homework

### Problems

- **problem_id** (integer): Primary key for each problem
- **assignment_id** (integer): Foreign key to the Assignments table
- **homework_id** (integer): Foreign key to the Homework table
- **name** (string): Name of the problem

### Students_Lectures

- **student_id** (integer): Foreign key to the Students table
- **lecture_id** (integer): Foreign key to the Lectures table
- **attendance** (boolean): Whether the student attended the lecture
- **problem_solved** (integer): Number of problems solved by the student for the lecture

### Instructors

- **instructor_id** (integer): Primary key for each instructor
- **name** (string): Name of the instructor
- **email** (string): Email address of the instructor