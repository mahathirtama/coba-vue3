<template>
    <NavBar />
    <form-create-vue />
</template>

<script>
import NavBar from '@/components/Navbar.vue'
import FormCreateVue from '@/components/FormCreate.vue'
export default {
    name: 'CreateView',
    components: {
        NavBar,
        FormCreateVue
    }
}
</script>

<style scoped>

</style>