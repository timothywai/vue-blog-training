<template>
  <div class="blogs">
    <h1>All Blogs</h1>

    <article class="media" v-for="myblog in blogs">
          <div class="media-content">
            <div class="content">

              <p>
                  <router-link :to="'/blogs/' + myblog.id"><strong>{{ myblog.title }}</strong></router-link>
              </p>

            </div>
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
      blogs: [],
    }
  },
  computed:{},
  methods:{},
  mounted(){
    axios.get('http://localhost:8000/api/blogs').then(response=>{
      this.blogs = response.data;
    }).catch(error=>{
      console.log("Error in get all blogs");
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
