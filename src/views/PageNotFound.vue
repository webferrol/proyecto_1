<template>
<!-- BEM (Block-Element-Modifiers) nomenclature -->
    <section class="block-content">
        <h1 class="block-content__title">Página no encontrada</h1>
        <CustomerButton :parameter="{message:'hola'}" />
        <CustomerButton :callback="goAbout">About</CustomerButton>
    </section>
</template>


<script>
import CustomerButton from "@/components/CustomerButton.vue"

export default {
    components:{
        CustomerButton
    },
    methods:{
        goAbout(){
           this.$router.push('/about');
        }
    }
}
</script>