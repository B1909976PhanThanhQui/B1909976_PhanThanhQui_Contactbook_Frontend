<template>
    <div  class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="createContact" />
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
            contact: {    

            },
            message: "",
        };
    },
    methods: {
        async createContact() {
            try {
                await ContactService.create(this.contact)
                this.message = "Liên hệ được tạo thành công.";
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
