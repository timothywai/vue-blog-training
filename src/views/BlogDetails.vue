<template>
  <div class="blogs">
    <h1>{{ blog.title }}</h1>

    <article class="media" >

          <div class="media-content">

            <div class="content">
              <p>{{ blog.content }}</p>
            </div>

            <article class="media" v-for="comment in blog.comments">
              <figure class="media-left"></figure>
                <div class="content">
                  <strong>Comment:</strong><br/>
                  {{ comment }}
                </div>
            </article>

          </div>
    </article>

  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';


export default {
  data() {
    return {
      blog: [],
    }
  },
  computed:{},
  methods:{},
  mounted(){
    // console.log(this.$route.params.id);
    axios.get('http://localhost:8000/api/blogs/' + this.$route.params.id).then(response=>{
      // console.log(response.data);
      this.blog = response.data;
    }).catch(error=>{
    console.log("Error in get all comments");
    });
  },
};
</script>

<style scoped>
.blogs {
  font-size: 20;
  text-align: left;
  margin-left: 20px;
}

.blogs h1 {
  font-size: 28px;
  font-weight: 600;
}

</style>
