<template>
  <div class="app-list">
    <div class="app-item" v-for="app in apps" :key="app.name" v-on:click="onClick(app)">
      <img :alt="app.name" :src="app.image" />
    </div>
  </div>
</template>

<script>
export default {
  name: "SamsungTVApps",
  props: {
    apps: Array
  },
  methods: {
    onClick: appObs => {
      const app = JSON.parse(JSON.stringify(appObs));
      fetch(`${process.env.VUE_APP_SAMSUNG_TV_API}/apps/${app.key}`)
        .then(() => {
          alert(`Samsung TV open ${app.key} application sent`);
        })
        .catch(error => {
          alert(error);
        });
    }
  }
};
</script>

<style scoped>
.app-list {
  display: inline-block;
}
.app-list .app-item {
  display: inline-block;
  margin-right: 5px;
  cursor: pointer;
}
.app-list .app-item:hover {
  opacity: 0.5;
}
.app-list .app-item img {
  height: 100px;
  width: 100px;
}
</style>
