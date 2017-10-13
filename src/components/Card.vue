<template lang="html">
  <div class="card">
    <div class="card-content">
      <img :src="collection.imageUrl" :alt="collection.collector">
      <h4></h4>
      <p></p>s
    </div>
  </div>
</template>

<script>
export default {
  props: ['collection'],
  name: 'card'
};
</script>

<style lang="css">
  .card {
    background: #F5F5F5;
    padding: 10px;
    margin: 0 0 1em;
    width: 100%;
    cursor: pointer;
    transition: all 100ms ease-in-out;
  }
  .card:hover {
    transform: translateY(-0.5em);
    background: #EBEBEB;
  }
  img {
    display: block;
    width: 100%;
  }
</style>
