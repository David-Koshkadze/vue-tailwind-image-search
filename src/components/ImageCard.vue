<template>
  <div class="max-w-sm rounded shadow-lg mx-auto">
    <img :src="image.webformatURL" alt class="w-full" />
    <div class="px-6 py-4">
      <p class="text-purple-600">Photo by {{image.user}}</p>
      <ul>
        <li>
          <strong>Views:</strong>
          {{image.views}}
        </li>
        <li>
          <strong>Likes:</strong>
          {{image.likes}}
        </li>
        <li>
          <strong>Downloads:</strong>
          {{image.downloads}}
        </li>
      </ul>
      <div class="py-2">
        <span v-for="(tag, idx) in tags" :key="idx" 
          class="bg-green-300 text-green-900 rounded-full px-2 py-1 mr-3"
        >#{{tag}}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageCard",
  props: ["image"],
  data() {
    return {
      tags: this.image.tags.split(',')
    };
  }
};
</script>