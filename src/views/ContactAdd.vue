<template>
    <div class="page">
        <h4>THÊM MỚI LIÊN HỆ</h4>
        <ContactForm @submit:contact="addContact"/>
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
            contact: null,
            message: "",
        };
    },
    methods: {
            async addContact(data) {
      try {
        await ContactService.create(data);
        this.message = "Liên hệ được thêm thành công.";
      } catch (error) {
        console.log(error);
            }
        },
    },
    created() {
        this.message = "";
    },
};
</script>