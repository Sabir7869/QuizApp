**Online Quiz Platform Backend**
This project provides a robust and scalable backend for an online quiz application, built using Spring Boot. It offers comprehensive functionalities for managing a question bank, creating dynamic quizzes, delivering questions securely, and calculating quiz results.

🚀 Features
Question Management:

Add new questions (title, options, answer, category, difficulty).

Retrieve all questions or filter by category.

Get a specific question by ID.

Delete questions by ID or clear all questions.

Get total question count.

Quiz Management:

Create quizzes dynamically by specifying category and number of questions.

Fetch quiz questions for users (answers are hidden).

Submit user responses and calculate scores.

🛠️ Technologies Used
Java 17+

Spring Boot 3.x

Spring Data JPA

Hibernate

RESTful APIs

PostgreSQL (or H2 for local development)

Maven

Lombok

🏁 Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

Prerequisites
Java Development Kit (JDK) 17 or higher

Maven

(Optional) PostgreSQL database instance, or it will default to H2 in-memory database.

Installation
Clone the repository:

git clone https://github.com/your-username/online-quiz-app-backend.git
cd online-quiz-app-backend

(Replace your-username with your actual GitHub username and online-quiz-app-backend with your repository name)

Configure Database (Optional - for PostgreSQL):
If you're using PostgreSQL, update your src/main/resources/application.properties (or application.yml) with your database credentials:

spring.datasource.url=jdbc:postgresql://localhost:5432/your_database_name
spring.datasource.username=your_username
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update # or create
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

If you don't configure PostgreSQL, Spring Boot will use an in-memory H2 database by default.

Build the project:

mvn clean install

Run the application:

mvn spring-boot:run

The application will start on http://localhost:8080 by default.

💡 API Endpoints
The API base URL is http://localhost:8080.

Question Endpoints (/question)
GET /question/all

Retrieves all questions.

Example: GET http://localhost:8080/question/all

GET /question/category/{category}

Retrieves questions by category.

Example: GET http://localhost:8080/question/category/Java

GET /question/{id}

Retrieves a question by its ID.

Example: GET http://localhost:8080/question/1

POST /question/add

Adds a new question.

Request Body (JSON):

{
    "questionTitle": "What is Spring Boot?",
    "optionA": "A framework for building web apps",
    "optionB": "A database",
    "optionC": "A programming language",
    "optionD": "An operating system",
    "answer": "A framework for building web apps",
    "category": "Spring",
    "difficultyLevel": "Easy"
}

DELETE /question/delete/{id}

Deletes a question by ID.

Example: DELETE http://localhost:8080/question/delete/1

DELETE /question/clear

Clears all questions from the database.

Example: DELETE http://localhost:8080/question/clear

GET /question/totalCount

Gets the total number of questions.

Example: GET http://localhost:8080/question/totalCount

Quiz Endpoints (/quiz)
POST /quiz/create

Creates a new quiz.

Parameters: category (String), numQ (int), title (String)

Example: POST http://localhost:8080/quiz/create?category=Java&numQ=5&title=Java%20Basics%20Quiz

GET /quiz/get/{id}

Retrieves questions for a specific quiz (answers are hidden).

Example: GET http://localhost:8080/quiz/get/1

POST /quiz/submit/{id}

Submits user responses for a quiz and calculates the score.

Request Body (JSON):

[
    {
        "id": 1,
        "response": "Option A"
    },
    {
        "id": 2,
        "response": "Option C"
    }
]

Example: POST http://localhost:8080/quiz/submit/1

🤝 Contributing
Feel free to fork the repository, create a new branch, and submit pull requests. Any contributions are welcome!

