<script setup>
definePageMeta({
  title: "Edit Book",
});

// /edit/1
const paramID = useRoute().params.id;

// // /edit?id=1
// const queryID = useRoute().query.id;

const form = ref({
  bookName: "",
  bookSynopsis: "",
  bookAuthor: "",
  bookFeatured: false,
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
]);

form.value.bookName = bookData.value[0].bookName;
form.value.bookSynopsis = bookData.value[0].bookSynopsis;
form.value.bookAuthor = bookData.value[0].bookAuthor;

const submit = () => {
  if (form.value.bookName == "" || form.value.bookAuthor == "") {
    return;
  }

  console.log(form.value);
};

// function submit() {
//   console.log(form.value);
// }
</script>
<template>
  <div>
    <rs-card>
      <template #header> Edit Book </template>
      <template #body>
        <FormKit
          type="form"
          :actions="false"
          @submit="submit"
          :incomplete-message="false"
        >
          <FormKit
            v-model="form.bookName"
            type="text"
            label="Book Name"
            validation="required"
            validation-visibility="dirty"
            :validation-messages="{
              required: 'Nama buku tidak boleh kosong',
            }"
          >
            <template #label>
              Book Name <span class="text-red-500">*</span>
            </template>
          </FormKit>
          <FormKit
            v-model="form.bookSynopsis"
            type="textarea"
            label="Book Synopsis"
            rows="10"
          />
          <FormKit
            v-model="form.bookAuthor"
            type="text"
            label="Book Author"
            validation="required"
            validation-visibility="dirty"
            :validation-messages="{
              required: 'Pengarang buku tidak boleh kosong',
            }"
          />
          <rs-button @click="submit"> Submit </rs-button>
        </FormKit>
      </template>
    </rs-card>
  </div>
</template>
