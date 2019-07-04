<template>
  <div class="home">
    <h1>Subscribe</h1>
    <p>Esterling Accime's mailing list</p>
    <el-input placeholder="Email..." v-model="input" clearable></el-input>
    <el-button>Subscribe</el-button>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'home',
  data() {
    return {
      input: '',
    };
  },
  components: {},
};
</script>


<style>
  .home {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 70vh;
    width: 40%;
    margin: 0 auto;
  }

  .home p {
    margin-top: 10px;
  }

  .home input {
    margin-top: 20px;
  }

  .home button {
    margin-top: 20px;
  }
</style>
