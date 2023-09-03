<template>
  <div class="card" style="width: 18rem">
    <img :src="poster" class="card-img-top" />
    <div class="card-body">
      <h5 class="card-title">{{ title }}</h5>
      <p class="card-text">
      </p>
      <a href="#" class="btn btn-primary">Ver mais</a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    poster: String,
    overview: String,
  },
};
</script>

<style>
.card {
  background-color: #fff;
  padding: 15px;
  transition: all 0.3s ease-in-out;
}

.card:hover {
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.75);
    transform: scale(1.05);
}
</style>