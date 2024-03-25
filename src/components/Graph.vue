<script>
export default {
  props: {
    imageUrl: {
      type: String,
      required: true,
    }
  },
  data() {
    return{
      img: null,
    }
  },
  methods: {
    async fetchImage() {
      try {
        const response = await fetch(this.imageUrl);
        if (response.ok) {
          const blob = await response.blob();
          this.img = URL.createObjectURL(blob);
        } else {
          console.error('Failed to fetch image:', response.status);
        }
      } catch (error) {
        console.error('Error fetching image:', error);
      }
    }
  },
  mounted() {
    this.fetchImage();
  },
}
</script>

<template>
  <div>
    <h2>Gráfica</h2>
    <img :src="img" alt="Imagen">
  </div>

</template>

<style scoped>

</style>
