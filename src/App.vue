<script setup>
import { reactive, ref } from "vue";
import Books from "./components/Books.vue";
import BookProgress from "./components/BookProgress.vue";
import AddBook from "./components/AddBook.vue";

let books = reactive([
  {
    id: 1,
    title: "History of Europe",
    cover:
      "https://www.presenca.pt/cdn/shop/products/image-1_c64f337f-8164-430c-b770-ad582280f726_grande.jpg?v=1607092126",
    isRead: true,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo",
  },
  {
    id: 2,
    title: "Penguin Classics",
    cover: "https://m.media-amazon.com/images/I/91cKrZxBuwL.jpg",
    isRead: false,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo, Jon Snow",
  },
  {
    id: 3,
    title: "Becoming",
    cover: "https://images-us.bookshop.org/ingram/9784087861174.jpg?v=enc-v1",
    isRead: false,
    isbn: "0-395-07157-8",
    author: "Daniel Trejo",
  },
  {
    id: 4,
    title: "Death Stranding 2: On the Beach",
    cover:
      "https://m.media-amazon.com/images/M/MV5BYmVkNDM3MzUtN2YyYS00MDg0LWIxN2EtMjQ2ZGQ1ZDhlZWY4XkEyXkFqcGc@._V1_.jpg",
    isRead: false,
    isbn: "0-395-07157-8",
    author: "Kojima-san",
  },
]);

function addBook(newBook) {
  newBook.id = Math.max(...books.map((el) => el.id)) + 1;
  books.push(newBook);
  showAddBook.value = false;
}

function toggleisRead(id) {
  books.forEach((book) => {
    if (book.id === id) {
      book.isRead = !book.isRead;
    }
  });
}

let showAddBook = ref(false);
</script>

<template>
  <div v-if="!showAddBook" class="container">
    <h1>📖 Meus Livros</h1>
    <div class="header-btns">
      <button class="btn" @click="showAddBook = !showAddBook">
        Adicionar Livro +
      </button>
    </div>

    <div class="books-container">
      <Books @toggleisRead="toggleisRead" :books="books" />
    </div>
    <BookProgress :books="books" />
  </div>
  <div v-else class="container">
    <AddBook @addBook="addBook" @closeAddBook="showAddBook = false" />
  </div>
</template>

<style scoped></style>
