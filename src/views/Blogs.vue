<template>
  <div class="about">
    <h1>This is an blogs page</h1>

    <p class="myinput">Message is: {{ msg }}</p>

    <input v-model="msg" placeholder="fill me" >

    <br /><br />
    <button :disabled="!isCompleted" class="btn btn-primary btn-block">Filled</button>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  data() {
    return {
      msg: '',
    }
  },
  computed:{
    isCompleted() {
        if (this.msg.length > 7 ) {
          return true;
        }
        return false ;
    }
  },
};
</script>

<style scoped>
.myinput {
  color: red;
}

</style>
