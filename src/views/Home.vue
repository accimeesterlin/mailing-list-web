<template>
  <div class="home">
    <h1>Subscribe</h1>
    <p>Esterling Accime's mailing list</p>
    <el-input placeholder="Email..." v-model="email" clearable></el-input>
    <el-button @click="subscribe" :loading="loading">Subscribe</el-button>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';

export default {
  name: 'home',
  data() {
    return {
      email: '',
      isError: false,
      loading: false,
    };
  },
  components: {},
  methods: {
    subscribe() {
      const { email } = this;
      const url = 'https://p2ylriihj6.execute-api.us-east-1.amazonaws.com/Prod/subscribe';
      this.loading = true;

      axios({
        url: `https://cors-anywhere.herokuapp.com/${url}`,
        method: 'POST',
        data: {
          email,
        },
      })
        .then(() => {
          this.isError = false;
          this.loading = false;

          this.$router.push('/confirmation');
        })
        .catch(() => {
          this.loading = false;
          this.isError = true;
        });
    },
  },
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
