<template>
  <div id="app">
    <header>
      <span>Vue.js PWA</span>
    </header>
    <main>
      <img src="./assets/logo.png" alt="Vue.js PWA">
      <card></card>
    </main>
  </div>
</template>

<script>
import cloudinary from 'cloudinary-core';
import data from './db.json';
import Card from './components/Card';
export default {
  name: 'app',
  data() {
    return {
      cloudinary: null,
      collections: []
    };
  },
  created() {
    this.cloudinary = cloudinary.Cloudinary.new({
      cloud_name: 'bigdevo'
    });
    this.collections = data.map(this.transform);
  },
  methods: {
    transform(collection) {
      const imageUrl = this.cloudinary.url(collection.imageId, {
        width: 300,
        crop: 'fit',
        quality: 'auto',
        secure: true
      });
      return Object.assign(collection, { imageUrl });
    }
  },
  components: {
    Card
  }
};
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: center;
  margin-top: 40px;
}

header {
  margin: 0;
  height: 56px;
  padding: 0 16px 0 24px;
  background-color: #35495E;
  color: #ffffff;
}

header span {
  display: block;
  position: relative;
  font-size: 20px;
  line-height: 1;
  letter-spacing: .02em;
  font-weight: 400;
  box-sizing: border-box;
  padding-top: 16px;
}
</style>
