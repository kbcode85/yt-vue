<template>
  <div>
    <input @input="onInput"/>
    <button class="btn btn-primary" @click="onClick">Szukaj</button>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data() {
    return {
      text: ""
    }
  },
  methods: {
    onInput: function(event) {
      this.text = event.target.value
    },
    onClick: function(){
      this.$emit('termChange', this.text);
    }
  }
}
</script>

<style scoped>
input {
  width: 75%;
}
div {
  text-align: center;
  margin: 20px;
}
</style>
