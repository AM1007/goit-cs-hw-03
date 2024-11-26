# Homework for the module "Introduction to Database Management Systems"

The homework consists of two independent tasks and may seem quite large in volume, but there’s no need to worry as we have detailed hints and recommendations for completing the tasks.

## Technical Description of the Tasks

### Task 1

Create a database for a task management system using PostgreSQL. The database should contain tables for users, task statuses, and tasks themselves. Perform the necessary queries in the task management database.

#### Step-by-step Instructions

1. Create tables in your PostgreSQL database according to the requirements. Use appropriate data types and constraints.

##### Database structure requirements:

**Table `users`:**

- `id`: Primary key, auto-increment (type `SERIAL`)
- `fullname`: Full name of the user (type `VARCHAR(100)`)
- `email`: User's email address, which must be unique (type `VARCHAR(100)`)

**Table `status`:**

- `id`: Primary key, auto-increment (type `SERIAL`)
- `name`: Status name (type `VARCHAR(50)`), should be unique. We suggest the following status types: [('new',), ('in progress',), ('completed',)].

**Table `tasks`:**

- `id`: Primary key, auto-increment (type `SERIAL`)
- `title`: Task title (type `VARCHAR(100)`)
- `description`: Task description (type `TEXT`)
- `status_id`: Foreign key pointing to `id` in the `status` table (type `INTEGER`)
- `user_id`: Foreign key pointing to `id` in the users table (type `INTEGER`)

2. Make sure the `email` field in the `users` table and the `name` field in the `status` table are unique.

3. Set up the relationships between the tables so that when a user is deleted, all their tasks are automatically deleted (cascading delete).

4. Write the script to create these tables.

5. Write the seed.py script in Python to populate these tables with random values. Use the Faker library.

6. Using SQL, execute the following queries in the task management database.

#### Queries to execute:

- **Get all tasks for a specific user**. Use `SELECT` to get tasks for a specific user by their `user_id`.
- **Select tasks with a specific status**. Use a subquery to select tasks with a specific status, such as `'new'`.
- **Update the status of a specific task**. Change the status of a specific task to `'in progress'` or another status.
- **Get a list of users with no tasks**. Use a combination of `SELECT`, `WHERE NOT IN`, and a subquery.
- **Add a new task for a specific user**. Use `INSERT` to add a new task.
- **Get all tasks that are not completed**. Select tasks whose status is not `'completed'`.
- **Delete a specific task**. Use `DELETE` to remove a task by its `id`.
- **Find users with a specific email address**. Use `SELECT` with a `LIKE` condition to filter by email.
- **Update a user's name**. Change a user's name using `UPDATE`.
- **Get the number of tasks for each status**. Use `SELECT`, `COUNT`, `GROUP BY` to group tasks by their status.
- **Get tasks assigned to users with a certain email domain**. Use `SELECT` with a `LIKE` condition combined with `JOIN` to select tasks assigned to users whose email contains a specific domain (e.g., '%@example.com').
- **Get a list of tasks with no description**. Select tasks that have no description.
- **Select users and their tasks that are in `'in progress'` status**. Use `INNER JOIN` to get users and their tasks with a specific status.
- **Get users and the number of their tasks**. Use `LEFT JOIN` and `GROUP BY` to select users and count their tasks.

> [!TIP] Recommendations for Execution:
> Use your SQL skills to formulate and execute each of these queries in your database.
> Ensure you understand how each query works and what results you should expect to get.
> For a better understanding, try modifying the queries or creating your own based on the database structure.

---

### Task 2

Develop a Python script that uses the PyMongo library to implement basic CRUD (Create, Read, Update, Delete) operations in MongoDB.

#### Step-by-step Instructions

1. Create a database according to the requirements.

##### Database structure requirements:

2. Each document in your database should have the following structure:

```JSON
{
    "_id": ObjectId("60d24b783733b1ae668d4a77"),
    "name": "barsik",
    "age": 3,
    "features": ["ходить в капці", "дає себе гладити", "рудий"]
}
```

The document represents information about a cat, including its `name`, `age`, and `features`.

2. Develop a main.py Python script to perform the following tasks.

#### Tasks to perform:

**Reading (Read):**

- Implement a function to display all records from the collection.
- Implement a function that allows the user to enter the cat's name and display information about that cat.

**Updating (Update):**

- Create a function that allows the user to update a cat's age by name.
- Create a function that allows adding a new feature to the cat's features list by name.

**Deleting (Delete):**

- Implement a function to delete a record from the collection by the animal's name.
- Implement a function to delete all records from the collection.

> [!TIP] Recommendations for Execution:
>
> - Use MongoDB Atlas or a locally installed MongoDB instance via Docker.
> - Install the PyMongo library via pip or another package manager like pipenv or poetry.
> - Don't forget to handle possible exceptions when performing database operations.
> - Ensure your functions are clearly commented and well-structured.
> - It's encouraged to use a Python virtual environment to isolate project dependencies.
