<template>
  <button class="btn" @click="onClick()" :style="{ background: colour }">
    {{ text }}
  </button>
</template>

<script>
  export default {
    name: "Button",
    props: {
      text: String,
      colour: String,
    },
    methods: {
      onClick() {
        this.$emit("btn-click");
      },
    },
  };
</script>
