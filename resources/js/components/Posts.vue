<template>
  <main>
    <div class="container">
      <h1>Posts</h1>
       
       <SinglePost
       v-for="post in posts"
       :key="post.id"
       :post="post" 
       />

    </div>
  </main>
</template>

<script>
import SinglePost from './SinglePost.vue';

export default {
  name: "Posts",

  components:{
    SinglePost
  },

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