<script setup>
definePageMeta({
  title: "bookstore",
});

const bookData = ref([
  {
    bookID: 1,
    bookName: "The Lord of the Rings",
    bookSynopsis:
      "The Lord of the Rings is an epic high-fantasy novel written by English author and scholar J. R. R. Tolkien.",
    bookAuthor: "Adi Iman",
    bookFeatured: true,
  },
  {
    bookID: 2,
    bookName: "The Lord of the Rings 2",
    bookSynopsis:
      "The Lord of the Rings is an epic high-fantasy novel written by English author and scholar J. R. R. Tolkien.",
    bookAuthor: "Adi Iman",
    bookFeatured: true,
  },
  {
    bookID: 3,
    bookName: "The Lord of the Rings 3",
    bookSynopsis:
      "The Lord of the Rings is an epic high-fantasy novel written by English author and scholar J. R. R. Tolkien.",
    bookAuthor: "Adi Iman",
    bookFeatured: false,
  },
  {
    bookID: 4,
    bookName: "The Lord of the Rings 4",
    bookSynopsis:
      "The Lord of the Rings is an epic high-fantasy novel written by English author and scholar J. R. R. Tolkien.",
    bookAuthor: "Adi Iman",
    bookFeatured: false,
  },
]);
</script>
<template>
  <div>
    <p
      class="flex justify-between items-start md:items-center mb-4 flex-col md:flex-row"
    >
      <span class="text-2xl font-bold">Bookstore List</span>
      <nuxt-link to="/bookstore/add">
        <rs-button>
          <Icon name="material-symbols:add"></Icon>
          Add New
        </rs-button>
      </nuxt-link>
    </p>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-x-6">
      <rs-card class="p-5 relative" v-for="(val, index) in bookData">
        <rs-badge
          v-if="val.bookFeatured == true"
          variant="warning"
          class="absolute top-3 -right-3"
        >
          Featured
        </rs-badge>
        <h5>
          {{ val.bookName }}
        </h5>
        <p class="">
          {{ val.bookSynopsis }}
        </p>
        <br />
        <br />
        <span>Author: {{ val.bookAuthor }}</span>

        <nuxt-link :to="`/bookstore/edit/${val.bookID}`">
          <rs-button size="sm" class="mt-2"> Edit </rs-button>
        </nuxt-link>
      </rs-card>
    </div>
  </div>
</template>
