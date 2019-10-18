<template>
  <div>
    <input @input="sendKeyWordToApp" />
  </div>
</template>

<script>

export default {
  name: "Search_Bar",
  methods: {
    sendKeyWordToApp(e){
      this.$emit('termChange', e.target.value)
    }
  }
};
</script>

<style scoped>
  input{
    width: 75%;
  }
  div{
    text-align: center;
    margin: 20px;
  }
</style>