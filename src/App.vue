<template>
  <div class="container mx-auto">
    <SearchComp @search-img="formSubmitted" />
    <div v-if="isLoading" class="text-center text-4xl mt-8">Loading...</div>
    <div v-if="!isLoading" class="grid grid-cols-1 sm:grid-cols-3 gap-4">
      <ImageCard v-for="(image, index) in images" :key="index" :image="image" />
    </div>
    <div v-if="!isLoading && !images.length" class="text-center text-4xl mt-8">Not Found</div>
  </div>
</template>

<script>
import SearchComp from "./components/SearchComp";
import ImageCard from "./components/ImageCard";

export default {
  name: "App",
  components: {
    SearchComp,
    ImageCard
  },
  data: () => ({
    images: [],
    isLoading: true
  }),
  methods: {
    formSubmitted(text) {
      fetch(
        `https://pixabay.com/api/?key=${process.env.VUE_APP_API_KEY}&q=${text}&image_type=photo`
      )
        .then(res => res.json())
        .then(data => {
          this.isLoading = false;
          this.images = [...data.hits];
        })
        .catch(err => console.log(err));
    }
  }
};
</script>
