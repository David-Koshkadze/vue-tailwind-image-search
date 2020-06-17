<template>
  <div class="text-center m-4">
    <form @submit.prevent="$emit('search-img', searchText)">
      <input
        type="text"
        placeholder="Search Image"
        v-model="searchText"
        class="border border-gray-300 rounded py-2 px-1 w-64"
      />
      <button
        type="submit"
        class="bg-green-600 text-white text-semibold px-3 py-2 rounded ml-2"
      >Search</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchComp",
  data() {
    return {
      searchText: ""
    };
  }
};
</script>

<style>
</style>