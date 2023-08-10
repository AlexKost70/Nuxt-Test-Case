<template>
  <main>
    <Card v-for="item in data"
      :id="item._id"
      :key="item.index"
      :picture="item.picture"
      :age="item.age"
      :name="item.name"
      :email="item.email"
      :phone="item.phone"
      :about="item.about"
    />
  </main>
</template>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
  }

  :root {
    --gray: #BDBDBD;
    --black: #333;
    --white: #ffffff;
  }

  main {
    max-width: 1280px;
    margin: 25vh auto;
    display: flex;
    flex-wrap: wrap;
    gap: 70px;
    align-items: center;
  }

  @media (max-width: 1280px) {
    main {
      justify-content: center;
    }
  }

  @media (max-width: 768px) {
    main {
      margin: 50px auto;
    }
  }
</style>

<script>
  import axios from 'axios';
  import Card from "./Card.vue"
  export default {
    name: "Main",
    data() {
      return {
        data: null,
      };
    },
    methods: {
      async fetchData() {
        axios
          .get('https://api.allorigins.win/raw?url=https://layout.solvintech.ru/nuxt/api', {
            method: 'GET',
            mode: 'no-cors',
            withCredentials: true,
            credentials: 'same-origin',
          })
          .then((response) => {
            this.data = response.data;
          })
          .catch((error) => {
            console.error(error);
          });
      }
    },
    mounted() {
      this.fetchData();
    },
  };
</script>
