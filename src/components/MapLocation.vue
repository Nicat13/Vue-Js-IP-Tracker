<template>
  <div id="maparea">
    <iframe
      v-show="showMap"
      :src="urlChanged"
      width="100%"
      height="100%"
      frameborder="0"
    ></iframe>
    <div v-show="!showMap">
      <b-spinner type="grow" label="Loading..."></b-spinner>
    </div>
  </div>
</template>

<script>
export default {
  props: ["url"],
  data() {
    return {
      showMap: false,
    };
  },
  computed: {
    urlChanged() {
      this.showMap = false;
      setTimeout(() => {
        this.showMap = true;
      }, 1500);
      return this.url;
    },
  },
};
</script>

<style scoped>
#maparea {
  height: 100vh;
  padding-top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>