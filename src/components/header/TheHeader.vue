<template>
  <nav>
    <button :class="{ clicked: showProjects }" @click="projects">
      Projects</button
    >|
    <button :class="{ clicked: showAddProjects }" @click="addProjects">
      Add Project
    </button>
  <h1>Welcome to Weekly Planner! </h1>
    <p>Plan your tasks with this nifty and handy planner</p>
    <p>Add or remove tasks with ease</p>


  </nav>
</template>

<script>
export default {
  data() {
    return {
      showProjects: true,
      showAddProjects: false,
    };
  },
  methods: {
    projects() {
      this.showProjects = true;
      this.showAddProjects = false;
      this.$emit("show", this.showProjects, this.showAddProjects);
    },
    addProjects() {
      this.showAddProjects = true;
      this.showProjects = false;
      this.$emit("show", this.showProjects, this.showAddProjects);
    },
  },
};
</script>

<style scoped>
nav {
  position: static;
  gap: 8%;
  margin-top: 2rem;
}

nav button {

  box-shadow: 0 0 0 10px hsl(0, 0%, 80%),
  0 0 0 15px hsl(0, 0%, 90%);
  background: #f24537 linear-gradient(to bottom, #f24537 5%, #c62d1f 100%);
  border-radius: 6px;
  cursor: pointer;
  border: 1px solid #d02718;
  margin: 1rem;
  font-size: 20px;
  font-weight: bold;
  padding: 6px 24px;
  text-shadow: 0 1px 0 #810e05;
}

nav button:hover
{
  animation: shake 0.82s cubic-bezier(.36,.07,.19,.97) both;
  transform: translate3d(0, 0, 0);
  perspective: 1000px;
}


@keyframes shake {
  10%, 90% {
    transform: translate3d(-1px, 0, 0);
  }
  20%, 80% {
    transform: translate3d(2px, 0, 0);
  }
  30%, 50%, 70% {
    transform: translate3d(-4px, 0, 0);
  }
  40%, 60% {
    transform: translate3d(4px, 0, 0);
  }
}

</style>