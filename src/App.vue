<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>
<script>
import axios from "axios"
export default {
  data() {
    return {
      msg: "[]",
    };
  },
  async mounted() {
    axios.get('/main.cfg').then(async  (response)=> {
      this.msg = response.data
      console.log(response.data)
    })
        .catch(error => {
          //this.errorMessage = error.message;
          console.log("There was an error!");
        });
  }
}

</script>


<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="main!" />
      <span>Содержимое конфига b2v: {{ msg }}</span>
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
