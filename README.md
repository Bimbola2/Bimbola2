<!DOCTYPE html>
<html>
<head>
  <title>Mi biblioteca de libros</title>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <h1>Mi biblioteca de libros</h1>

  <div id="book-list"></div>

  <form id="book-form">
    <input type="text" id="title" placeholder="Título del libro" required>
    <input type="text" id="author" placeholder="Autor del libro" required>
    <button type="submit">Añadir libro</button>
  </form>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  padding: 20px;
}

h1 {
  text-align: center;
}

#book-list {
  margin-top: 20px;
}

#book-form {
  margin-top: 20px;
}

#book-form input {
  margin-right: 10px;
}

#book-form button {
  margin-top: 10px;
}
// Array para almacenar los libros
let books = [];

// Función para añadir un libro
function addBook(event) {
  event.preventDefault();

  // Obtener los valores de los campos del formulario
  let titleInput = document.getElementById('title');
  let authorInput = document.getElementById('author');
  let title = titleInput.value;
  let author = authorInput.value;

  // Crear un objeto de libro
  let book = {
    title: title,
    author: author
  };

  // Añadir el libro al array
  books.push(book);

  // Limpiar los campos del formulario
  titleInput.value = '';
  authorInput.value = '';

  // Actualizar la lista de libros
  displayBooks();
}

// Función para mostrar los libros en la página
function displayBooks() {
  let bookList = document.getElementById('book-list');
  bookList.innerHTML = '';

  for (let i = 0; i < books.length; i++) {
    let book = books[i];
    let bookItem = document.createElement('div');
    bookItem.innerHTML = '<strong>' + book.title + '</strong> by ' + book.author;
    bookList.appendChild(bookItem);
  }
}

// Asociar el evento de envío del formulario a la función addBook
let form = document.getElementById('book-form');
form.addEventListener('submit', addBook);
