<template>
  <main>
    <div class="container">
      <h1>Posts</h1>
      
    </div>
  </main>
</template>

<script>
export default {
  name: "Posts",

  data(){
    return{
      apiUrl: 'http://127.0.0.1:8000/api/posts',
      posts: null
    }
  },

  mounted(){
    this.getPosts();
  },

  methods:{
    getPosts(){
      axios.get(this.apiUrl)
      .then(r => {

        this.posts = r.data;
        console.log(this.posts);
      })
      .catch(e =>{
        console.log(e);
      });
    }
  }
}
</script>

<style lang="scss" scoped>
main{
  padding: 40px 0;
}
</style>