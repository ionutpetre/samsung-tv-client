<template>
  <div class="tv-commands">
    <div class="tv-item-left">
      <img class="tv-image-big" :alt="tvData.key" :src="tvData.image" />
    </div>
    <div class="tv-item-right">
      <div
        class="tv-item-image"
        v-for="command in commands"
        v-bind:key="command.key"
        v-on:click="onClick(command)"
      >
        <img class="tv-image-small" :alt="command.key" :src="command.image" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SamsungTVCommands",
  props: {
    tvData: Object,
    commands: Array
  },
  methods: {
    onClick: function(commandObs) {
      const command = JSON.parse(JSON.stringify(commandObs));
      fetch(`${process.env.VUE_APP_SAMSUNG_TV_API}/tv/${command.key}`)
        .then(() => {
          alert(`Samsung TV ${command.key} command sent`);
        })
        .catch(error => {
          alert(error);
        });
    }
  }
};
</script>

<style scoped>
.tv-commands {
  height: 300px;
}
.tv-commands .tv-item-left {
  float: left;
  width: 70%;
}
.tv-commands .tv-item-right {
  float: right;
  width: 30%;
  padding-top: 50px;
}
.tv-commands .tv-image-big {
  height: 300px;
}
.tv-commands .tv-image-small {
  height: 100px;
  width: 100px;
  margin-bottom: 5px;
  cursor: pointer;
}
.tv-commands .tv-item-image:hover {
  opacity: 0.5;
}
</style>
