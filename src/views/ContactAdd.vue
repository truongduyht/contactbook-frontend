<template>
  <div class="page">
    <h4>Thêm liên hệ</h4>
    <ContactForm :contact="contact" @submit:contact="create" />
    <p>{{ message }}</p>
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
  components: {
    ContactForm,
  },
  data() {
    return {
      contact: {},
      message: "",
    };
  },
  methods: {
    async create(data) {
      try {
        await ContactService.create(data);
        this.message = "Tạo liên hệ thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
