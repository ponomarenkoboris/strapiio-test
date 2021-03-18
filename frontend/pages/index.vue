<template>
  <div class="container">
    <div class="items-container">
      <h1 class="title">Items</h1>
      <hr />
      <div class="items-wrapper">
        <div class="item" :key="data.id" v-for="data in dataArr">
          <strong>{{ data.title }}</strong>
          <small>{{ data.description }}</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainPage',
  async asyncData({ $axios }) {
    const items = await $axios.get('http://localhost:1337/items')
    const dataArr = await items.data
    return { dataArr }
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
.items-wrapper {
  width: 600px;
}
.item {
  text-align: left;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
}
</style>
