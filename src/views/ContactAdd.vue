<template>
    <ContactForm :contact="contact" @submit:contact="registerContact"/>
</template>

<script>
import ContactForm from '@/components/ContactForm.vue';
import ContactServices from '@/services/contact.services';

    export default  {
        data() {
            return {
                contact: {}
            }
        },
        components: {
            ContactForm
        },
        methods: {
            async registerContact(data) {
                try {
                    await ContactServices.create(data);
                    alert("Liên hệ được tạo thành công!");
                    this.$router.push({ name: "contactbook" });
                } catch (error) {
                    console.log(error)
                }
            }
        }
    }
</script>