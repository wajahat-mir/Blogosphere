<template>
    <div class="article-containers">
        <span>{{ article.title }} - {{ article.author }} {{ article.publishdate }}</span>
        <p>
        {{ article.body }}
        </p>
    </div>
</template>

<script>
export default {
    props: {
        article: Object
    }
}
</script>

<style scoped>

</style>