<template>
  <div class="samsung-tv">
    <h1 class="title">{{ title }}</h1>
    <p class="description">{{ description }}</p>
    <SamsungTVCommands :tvData="tvData" :commands="commands" />
    <SamsungTVApps :apps="apps" />
  </div>
</template>

<script>
import SamsungTVCommands from "./SamsungTVCommands.vue";
import SamsungTVApps from "./SamsungTVApps.vue";

export default {
  name: "SamsungTV",
  props: {
    title: String,
    description: String
  },
  components: {
    SamsungTVCommands,
    SamsungTVApps
  },
  data() {
    return {
      tvData: {
        title: "Samsung TV",
        image: require("./../assets/images/samsung-tv.jpg")
      },
      commands: [
        {
          key: "open",
          image: require("./../assets/images/open-tv.png")
        },
        {
          key: "stop",
          image: require("./../assets/images/stop-tv.png")
        }
      ],
      apps: [
        {
          key: "youtube",
          image: require("./../assets/images/youtube.png")
        },
        {
          key: "netflix",
          image: require("./../assets/images/netflix.png")
        },
        {
          key: "hbogo",
          image: require("./../assets/images/hbogo.png")
        }
      ]
    };
  }
};
</script>

<style scoped>
.samsung-tv {
  width: 600px;
  height: 600px;
  display: inline-block;
  background: white;
  border-radius: 15px;
}
.samsung-tv .title {
  font-size: 46px;
}
.samsung-tv .description {
  font-size: 18px;
}
</style>
