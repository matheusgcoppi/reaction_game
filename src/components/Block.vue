<template>
  <div class="centered" @click.self="closeDiv">
    <p>Click me</p>
  </div>
</template>

<script>
export default {
  props: ['start'],
  data() {
    return {
      isClicked: true,
    }
  },
  methods: {
    closeDiv() {
      const end = Date.now();
      const result = end - this.start
      this.$emit('close', result);
    }
  }
}

</script>

<style scoped>
.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 500px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: green;
  border-radius: 20px;
}

div p {
  color: white;
  font-size: 20px;
}
</style>




