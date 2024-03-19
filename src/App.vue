
/* Create a template for showing news in a card 
 title should be bold and small font
 content should be displayed on hover of the card
 card should have light grey background and black text
*/


<template>
  <div>
    <h1>News</h1>
    <ul>
      <li v-for="article in articles" :key="article.id">
        <div class="card">
          <h2 class="card-title">{{ article.title }}</h2>
          <p class="card-content">{{ article.content }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
created() {
  this.fetchNews();
},
methods: {
  // Create a function to call the news API and store the string result in a variable
  async fetchNews() {
    try {
      const response = await fetch('https://localhost:7016/api/News');
      const data = await response.json();
      console.log(data);
      this.articles = data.articles;
    } catch (error) {
      console.error(error);
    }
  }
},
data() {
  return {
    articles: []
  };
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
