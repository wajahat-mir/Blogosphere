<template>
  <div id="app">
    <Header />
      <Article
        v-for="article in articles" :key="article.id"
        v:if="articles.length"
        :article="article"
      />
  </div>
</template>

<script>
import Article from './components/Article.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header,
    Article
  },
  data(){
    return{
      articles: []
    }
  },
  mounted: function(){
    fetch('https://thisAPIhasntbeendeveloped.com/articles',{
      method: 'get'
    })
    .then((response) => {
      console.log(response.json())
    })
    .then((jsonData) => {
      this.articles = jsonData.results
    })
    .catch((error) => {
      console.log(error)
    })
    .then(() => {
      this.articles =
        [
          { "id":1,"title":"Quarantine!","body":"Quarantine has been applied.","author":"James Bond","publishdate":"2020-05-17" },
          { "id":2,"title":"Quarantine!!","body":"Quarantine has been applied..","author":"James Bond!","publishdate":"2020-05-18" }
        ]
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
