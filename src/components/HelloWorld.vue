<template>
  <div class="photos">
    <div v-for="photo in photos" :key="photo.id" class="photo">
      <p>{{ photo.title }}</p>
      <img :src="photo.thumbnailUrl" :alt="photo.title" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      photos: [],
    };
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/photos?_start=0&_limit=100")
      .then((res) => {
        this.photos = res.data;
      });
  },
};
</script>

<style scoped>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.photos {
  margin-top: 20px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 50px;
}
.photo {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  border: 2px #ddd solid;
  border-radius: 50px;
  overflow: hidden;
}
.photo p{
  text-align: left;
}
.photo img{
  max-height: 100%;
  height: 100px;
  border-radius: 50px;
}
</style>
