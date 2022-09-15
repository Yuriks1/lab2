<template>
  <base-card :class="{ complete: isComplete }">

    <ul>
      <h2 @click="showDescription">{{ project.title }}</h2>
      <p v-if="showDesc">{{ project.description }}</p>
      <li>
        <div class="icons">
          <svg @click="deleteProject(project.title)" xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16">
            <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
            <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
          </svg>

          <svg @click="completeProject(project.title)" xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-check2-all" viewBox="0 0 16 16">
            <path d="M12.354 4.354a.5.5 0 0 0-.708-.708L5 10.293 1.854 7.146a.5.5 0 1 0-.708.708l3.5 3.5a.5.5 0 0 0 .708 0l7-7zm-4.208 7-.896-.897.707-.707.543.543 6.646-6.647a.5.5 0 0 1 .708.708l-7 7a.5.5 0 0 1-.708 0z"/>
            <path d="m5.354 7.146.896.897-.707.707-.897-.896a.5.5 0 1 1 .708-.708z"/>
          </svg>
        </div>
      </li>
    </ul>
  </base-card>
</template>
<script>
import baseCard from "./base/BaseCard.vue";
export default {
  data() {
    return {
      isComplete: this.project.isComplete,
      showDesc: true,
    };
  },
  components: {
    baseCard,
  },
  props: ["project"],
  emits: ["deleteProject", "completeProject"],
  methods: {
    deleteProject(title) {
      this.$emit("deleteProject", title);
    },
    completeProject(title) {
      this.$emit("completeProject", title);
      this.isComplete = !this.isComplete;
    },
    showDescription() {
      this.showDesc = !this.showDesc;
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  text-decoration: none;
}



svg {
  height: 2.5rem;
  width: 10rem;
  background: white;
  border-radius: calc( 3.5rem/2);
  margin-bottom: 0.5rem;
  box-shadow: black;
  border: 1px solid var(--color-bg-4);
}

svg:hover {
  color: red;
}

li {
  display: inline;
}
.icons {
  text-align: end;
}
.complete {
  border-left: 5px solid green;
}
</style>