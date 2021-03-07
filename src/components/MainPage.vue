<template>
  <div>
    <router-link :to="`/about/${this.id}`">
    <b-card
      bg-variant="light"
      text-variant="dark"
      :header="Name"
      class="text-center"
    >
      <b-img :src="Img"></b-img>
    </b-card></router-link>
  </div>
</template>

<script>
export default {
  props: {
    Name: String,
    Img: String,
    id: Number,
  },
};
</script>

<style>
</style>