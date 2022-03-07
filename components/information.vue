<template>
    <section class="container">
        <h2 class="title">Комментарии</h2>
        
        <comments />
        
    </section>
</template>

<script>
import comments from './comments.vue'
export default {
    
    data: () => ({
        comments,
    }),
}
</script>

<style scoped lang="scss">



</style>