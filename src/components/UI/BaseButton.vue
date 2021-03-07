<template>
  <button :class="mode" :type="type">
      <slot></slot>
  </button>
</template>

<script>
export default {
    props: ['type','mode'],

}
</script>

<style scoped>

button {
    background-color: brown;
    border: 1px solid brown;
    color:white;
    font-family: inherit;
    border-radius: 15px;
    padding: 1rem;
    margin: 1rem;
    cursor: pointer;
}

button:focus {
    outline:none;
}
button:hover,
button:active {
    background-color: white;
    color: brown;
}

.selectedButton {
    background-color: white;
    color: brown;
}

</style>