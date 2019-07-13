<template>
  <div class="home">
    <img src="/profile.PNG" alt="">
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
      errorMessage: '',
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
          latitude: this.latitude,
          longitude: this.longitude,
          zipCode: this.zipCode,
          timezone: this.timezone,
          ipAddress: this.ipAddress,
        },
      })
        .then(this.loadSuccessSusbcribe)
        .catch(this.loadFailSubscribe);
    },

    loadSuccessSusbcribe() {
      this.isError = false;
      this.loading = false;

      this.$router.push('/confirmation');
    },

    loadFailSubscribe(error) {
      this.loading = false;
      this.isError = true;
      this.errorMessage = error.message || 'Subscription failed, please try again later';
    },

    fetchCurrentLocation() {
      axios('http://ip-api.com/json')
        .then(this.getCurrentLocation)
        .catch(this.getCurrentLocationFail);
    },

    getCurrentLocation(response) {
      const { data } = response;
      this.latitude = data.lat;
      this.longitude = data.lon;
      this.zipCode = data.zip;
      this.timezone = data.timezone;
      this.ipAddress = data.query;
    },

    getCurrentLocationFail() {
      // TODO
      // Come up with a strategy
    },

  },

  mounted() {
    this.fetchCurrentLocation();
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
  width: 85%;
  margin: 0 auto;
  max-width: 760px;
}

img {
  width: 130px;
  border-radius: 50%;
  margin-bottom: 30px;
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
