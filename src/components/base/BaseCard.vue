<template>
  <div class="base">
    <slot></slot>
  </div>
</template>
<script>
export default {
};
</script>
<style scoped>

.base {
  border-left: 5px solid fuchsia;
}
header{

  width: 100vw;
  height: 100vh;
  position: absolute;
  top:5rem;
  border: solid;
  overflow: hidden;
}


div {
  display: grid;
  grid-template-columns: 60% 40%;
  gap: 8%;
  margin-top: 5rem;
  position: relative;
  border: solid;

}

div:hover{

  color: black;
}
</style>