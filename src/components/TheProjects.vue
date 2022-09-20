<template>
  <div class="buttons">
    <button @click="viewAllButton" :class="{ clicked: viewAll }">
      VIEW ALL
    </button>
    <button @click="completedButton" :class="{ clicked: completed }">
      COMPLETED
    </button>
    <button  @click="onGoingButton" :class="{ clicked: onGoing }">
      ONGOING
    </button>
  </div>

  <project-item
      v-for="project in projectsShow"
      :key="project.title"
      :project="project"
      @deleteProject="deleteProject"
      @completeProject="completeProject"
  ></project-item>
  <div class="headline"></div>


</template>


<script>
import projectItem from "./ProjectItem.vue";
export default {
  props: ["projects", "completedProjects", "isGoingProjects"],
  emits: ["deleteProject", "complete"],
  data() {
    return {
      viewAll: true,
      completed: false,
      onGoing: false,
      projectsShow: this.projects,
    };
  },
  components: {
    projectItem,
  },
  methods: {
    viewAllButton() {
      this.viewAll = true;
      this.completed = false;
      this.onGoing = false;
      this.projectsShow = this.projects;
    },
    completedButton() {
      this.viewAll = false;
      this.completed = true;
      this.onGoing = false;
      this.projectsShow = this.completedProjects;
    },
    onGoingButton() {
      this.viewAll = false;
      this.completed = false;
      this.onGoing = true;
      this.projectsShow = this.isGoingProjects;
    },
    deleteProject(index) {
      this.$emit("deleteProject", index);
    },
    completeProject(title) {
      this.$emit("completeProject", title);
    },
  },
};
</script>

<style scoped>
.buttons {
  text-align: right;
  gap: 3rem;
}

button,
a {
  cursor: pointer;
  box-shadow:inset 0 1px 0 0 #f5978e;
  background: #f24537 linear-gradient(to bottom, #f24537 5%, #c62d1f 100%);
  border-radius:6px;
  border:1px solid #d02718;
  display:inline-block;
  color:#ffffff;
  font-family: Arial, serif;
  font-size:15px;
  font-weight:bold;
  padding:6px 24px;
  text-decoration:none;
  text-shadow:0 1px 0 #810e05;
}

button:hover {
  cursor: pointer;
  color: black;
  box-shadow: 0 1rem 1rem rgba(0,0,0,0.4);
  transform: translateY(0.5rem);

}


</style>