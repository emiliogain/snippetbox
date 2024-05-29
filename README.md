# SnippetBox
SnippetBox is a web application written in Go that allows users to paste and share snippets of text. This project demonstrates various web development techniques and features including RESTful routing, middleware usage, dynamic HTML generation, MySQL database integration, stateful HTTP sessions, and secure user authentication.

![image](https://github.com/emiliogain/snippetbox/assets/104453967/97a9ef28-33f7-4306-9ee6-52c41338be11)

## Features

- **RESTful Routing**: Clean and organized URL routes that follow REST principles.
- **Middleware**: Middleware for request logging, secure headers, and more.
- **Dynamic HTML**: Server-side rendering of HTML templates.
- **MySQL Database**: Persistent storage of snippets and user data using MySQL.
- **Sessions**: Stateful HTTP sessions for maintaining user state across requests.
- **Secure User Authentication**: User authentication with password hashing and secure session management.

## Getting Started

### Prerequisites

- Go 1.16+
- MySQL 5.7+

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/emiliogain/snippetbox.git
   cd snippetbox

2. Set up the MySQL database:
   ```mysql
    CREATE DATABASE snippetbox;
    USE snippetbox;
   
    CREATE TABLE users (
    id INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    hashed_password CHAR(60) NOT NULL,
    created DATETIME NOT NULL,
    active BOOLEAN NOT NULL DEFAULT TRUE
    );
    ALTER TABLE users ADD CONSTRAINT users_uc_email UNIQUE (email);
   
    CREATE TABLE snippets (
    id INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(100) NOT NULL,
    content TEXT NOT NULL,
    created DATETIME NOT NULL,
    expires DATETIME NOT NULL
    );
    CREATE INDEX idx_snippets_created ON snippets(created);

3. Run the application:
   ```bash
   go run ./cmd/web

4. Visit http://localhost:4000 in your web browser to use the application.

## Usage

- **Create a Snippet**:
  1. Click the "Create Snippet" button on the homepage.
  2. Write a title and content for your snippet.
  3. Choose an expiration time: 1 year, 1 week, or 1 day.
  4. Click the "Publish Snippet" button to save and share your snippet.
     
![image](https://github.com/emiliogain/snippetbox/assets/104453967/332a14c2-80da-44d4-8a0e-43baab2f67ee)
![image](https://github.com/emiliogain/snippetbox/assets/104453967/88f40fa6-5bde-4108-ada6-a70ecb6564f5)


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Alex Edwards](https://www.alexedwards.net/) for his book "Let’s Go", which inspired this project.
- The Go community for providing extensive libraries and tools.
