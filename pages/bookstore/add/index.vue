<script setup>
definePageMeta({
  title: "Add New Book",
});

const form = ref({
  bookName: "",
  bookSynopsis: "",
  bookAuthor: "",
  bookFeatured: false,
});

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
      <template #header> Add Book </template>
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
