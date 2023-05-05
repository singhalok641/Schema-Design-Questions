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