<template>
    <!-- <div v-if="contact" class="page">
        <h4>Thêm Liên hệ Mới</h4>
        <ContactForm :contact="contact" @submit:contact="addContact" />
        <p>{{ message }}</p>
    </div> -->
    <div class="page">
        <h4>Thêm Liên hệ mới</h4>
        <ContactForm :contact="{}" @submit:contact="createContact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm2.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    // props: {
    //     id: { type: String, required: true },
    // },
    data() {
        return {
            // contact: null,
            message: "",
        };
    },
    methods: {
        // async getContact(id) {
        //     try {
        //         this.contact = await ContactService.get(id);
        //     } catch (error) {
        //         console.log(error);
        //         // Chuyển sang trang NotFound đồng thời giữ cho URL không đổi
        //         this.$router.push({
        //             name: "notfound",
        //             params: {
        //                 pathMatch: this.$route.path.split("/").slice(1)
        //             },
        //             query: this.$route.query,
        //             hash: this.$route.hash,
        //         });
        //     }
        // },
        async createContact(data) {
            try {
                // await ContactService.create(this.contact._id, data);
                await ContactService.create(data);
                alert('Liên hệ được thêm thành công.');
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.log(error);
            }
        },
    },
    created() {
        // this.getContact(this.id);
        this.message = "";
    },
};
</script>