---
author: Alaka A J
pubDatetime: 2025-03-09T16:10:00+00:00
title: Book Store Management System (MERN Stack) | Dev Notes
slug: book-store
featured: true
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - dev
  - mern
  - tutorial
  - react.js
  - vite
  - node.js
  - mongodb
  - express.js
description: Develop a simple Book Store Management Web Application using MERN Stack.
---

## Table of Contents

- [1. Create Node project from scratch](#1-create-node-project-from-scratch)
- [2. Create first HTTP request](#2-create-first-http-request)
- [3. Add MongoDB and Mongoose to Node.js](#3-add-mongodb-and-mongoose-to-nodejs)
- [4. Create Book Model with Mongoose](#4-create-book-model-with-mongoose)
- [5. Save a new Book with Mongoose](#5-save-a-new-book-with-mongoose)
- [6. Get all books with Mongoose](#6-get-all-books-with-mongoose)
- [7. Get One book by ID](#7-get-one-book-by-id)
- [8. Update a book](#8-update-a-book)
- [9. Delete a book](#9-delete-a-book)
- [10. Refactor with Express](#10-refactor-with-express)
- [11. CORS Policy](#11-cors-policy)
- [12. Create React project with Vite and Tailwind CSS](#12-create-react-project-with-vite-and-tailwind-css)
- [13. SPA and Add React Router DOM](#13-spa-and-add-react-router-dom)
- [14. Show Books list in React](#14-show-books-list-in-react)
- [15. Show Book Details](#15-show-book-details)
- [16. Create Book in React](#16-create-book-in-react)
- [17. Edit Book in React](#17-edit-book-in-react)
- [18. Delete Book in React](#18-delete-book-in-react)

## 1. Create Node project from scratch

- Create two folders for frontend and backend respectively. Till further steps, we will be working with backend folder.
- Install necessary packages:
  ```bash
  npm init -y        # to generate package.json
  ```
- Add `"type": "module"` to package.json
- Install express and nodemon:
  ```bash
  npm i express nodemon
  ```
- Add scripts to package.json:
  ```json
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js"
  }
  ```
- Create index.js file
- Add port details to config.js
- Start the server:
  ```bash
  npm run dev
  ```

## 2. Create first HTTP request

- Add a GET request handler to handle requests coming to root of the application:
  ```javascript
  app.get("/", (request, response) => {
    console.log(request);
    return response.status(234).send("status 234 from server");
  });
  ```

## 3. Add MongoDB and Mongoose to Node.js

- Add mongoDBURL to config.js
- Install Mongoose
- Use connect() to connect with the database

## 4. Create Book Model with Mongoose

- Use Schema() in mongoose to define the schema of book model
- Export the model

## 5. Save a new Book with Mongoose

- Import Book from models to index.js
  ```javascript
  app.post("/books", async (request, response) => {
    try {
      console.log(request.body);
      if (
        !request.body.title ||
        !request.body.author ||
        !request.body.publishedYear
      ) {
        return response
          .status(400)
          .send({
            message: "Make sure to answer all fields before submitting",
          });
      }
      const newBook = {
        title: request.body.title,
        author: request.body.author,
        publishedYear: request.body.publishedYear,
      };
      const book = await Book.create(newBook);
      return response.status(201).send({ message: `Book created ${book}` });
    } catch (error) {
      console.log(error);
    }
  });
  ```

## 6. Get all books with Mongoose

```javascript
app.get("/books", async (request, response) => {
  try {
    const books = await Book.find({});
    return response.status(200).json({
      count: books.length,
      data: books,
    });
  } catch (error) {
    console.log(error);
  }
});
```

## 7. Get One book by ID

```javascript
app.get("/books/:id", async (req, res) => {
  try {
    const { id } = req.params;
    const book = await Book.findById(id);
    return res.status(200).json(book);
  } catch (error) {
    console.log(error.message);
    return res.send(500).send({ message: error.message });
  }
});
```

## 8. Update a book

```javascript
app.put("/books/:id", async (request, response) => {
  try {
    if (
      !request.body.title ||
      !request.body.author ||
      !request.body.publishedYear
    ) {
      return response
        .status(400)
        .send({ message: "Make sure to answer all fields before submitting" });
    }

    const { id } = request.params;
    const result = await Book.findByIdAndUpdate(id, request.body);

    if (!result)
      return response.status(404).json({ message: "Book not found" });

    return response.status(200).send({ message: "Book updated successfully" });
  } catch (error) {
    console.log(error.message);
    return response.status(500).send({ message: error.message });
  }
});
```

## 9. Delete a book

```javascript
app.delete("/books/:id", async (request, response) => {
  try {
    const { id } = request.params;
    const result = await Book.deleteById(id);
    if (!result) return response.send(404).json({ message: "Book not found" });
    return response.status(200).send({ message: "Book deleted successfully" });
  } catch (error) {
    console.log(error.message);
    return response.status(500).send({ message: error.message });
  }
});
```

## 10. Refactor with Express

## 11. CORS Policy

- Allow all origins with default CORS configuration:
  ```javascript
  app.use(cors());
  ```
- Allow custom origins:
  ```javascript
  app.use(
    cors({
      origin: "localhost:3500",
      methods: ["GET", "PUT", "POST", "DELETE"],
      allowedHeaders: [],
    })
  );
  ```

## 12. Create React project with Vite and Tailwind CSS

```bash
npm create vite@latest
cd frontend
npm i
npm install tailwindcss @tailwindcss/vite
```

## 13. SPA and Add React Router DOM

```bash
npm i react-router-dom
```

## 14. Show Books list in React

- Install axios and react-icons

```javascript
useEffect(() => {
  setLoading(true);
  axios
    .get("http://localhost:5555/books")
    .then(response => {
      setBooks(response.data.data);
      setLoading(false);
    })
    .catch(error => {
      console.error("Error fetching books:", error);
      setLoading(false);
    });
  console.log(books);
}, []);
```

## 15. Show Book Details

```javascript
const [book, setBook] = useState([]);
const [loading, setLoading] = useState(false);
const { id } = useParams();

useEffect(() => {
  setLoading(true);
  axios
    .get(`http://localhost:5555/books/${id}`)
    .then(response => {
      setBook(response.data);
      setLoading(false);
    })
    .catch(error => {
      console.log(error);
      setLoading(false);
    });
}, []);
```

## 16. Create Book in React

```javascript
const handleBook = () => {
  const data = {
    title,
    author,
    publishedYear,
  };
  setLoading(true);
  axios
    .post("http://localhost:5555/books", data)
    .then(() => {
      setLoading(false);
      navigate("/");
    })
    .catch(error => {
      setLoading(false);
      alert("an error occured. couldn't add the book");
      console.log(error);
    });
};
```

## 17. Edit Book in React

```javascript
useEffect(() => {
  setLoading(true);
  axios
    .get(`http://localhost:5555/books/${id}`)
    .then(response => {
      setAuthor(response.data.author);
      setPublishedYear(response.data.publishedYear);
      setTitle(response.data.title);
      setLoading(false);
    })
    .catch(error => {
      setLoading(false);
      alert("an error occured. couldn't edit the book");
      console.log(error);
    });
}, []);

const handleBook = () => {
  const data = {
    title,
    author,
    publishedYear,
  };
  setLoading(true);
  axios
    .put(`http://localhost:5555/books/${id}`, data)
    .then(() => {
      setLoading(false);
      navigate("/");
    })
    .catch(error => {
      setLoading(false);
      alert("an error occured. couldn't add the book");
      console.log(error);
    });
};
```

## 18. Delete Book in React

```javascript
const handleBook = () => {
  setLoading(true);
  axios
    .delete(`http://localhost:5555/books/${id}`)
    .then(response => {
      setLoading(false);
      navigate("/");
    })
    .catch(error => {
      setLoading(false);
      console.log(error);
    });
};
```
