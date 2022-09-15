<template>
  <the-header @show="show"></the-header>
  <the-projects
      v-if="showProjects"
      :projects="projects"
      @deleteProject="deleteProject"
      @completeProject="completeProject"
      :completedProjects="completedProjects"
      :isGoingProjects="isGoingProjects"
  ></the-projects>
  <add-project v-if="this.showAddProject" @add="addProject"></add-project>
</template>

<script>
import TheHeader from "./components/header/TheHeader.vue";
import TheProjects from "./components/TheProjects.vue";
import AddProject from "./components/AddProject.vue";



export default {
  name: "App",
  components: {
    TheHeader,
    TheProjects,
    AddProject,
  },
  data() {
    return {
      showProjects: true,
      showAddProject: false,
      projects: [
        {
          title: "Plans for Monday:",
          isComplete: false,
          description: "Finish lab2, clean room",
        },
        {
          title: "Plans for Tuesday:",
          isComplete: false,
          description: "Finish lab3, wash clothes",
        },
        {
          title: "Plans for Wednesday:",
          isComplete: false,
          description: "Iron clothes, meet friends",
        },
        {
          title: "Plans for Thursday:",
          isComplete: false,
          description: "Study Java, meet sister",
        },
        {
          title: "Plans for Friday:",
          isComplete: false,
          description: "Study Vue, meet cousin",
        },
        {
          title: "Plans for Saturday:",
          isComplete: false,
          description: "Train, eat healthy",
        },
      ],
      completedProjects: [],
      isGoingProjects: [],
    };
  },
  methods: {
    show(showProjects, showAddProject) {
      this.showProjects = showProjects;
      this.showAddProject = showAddProject;
    },
    addProject(title, description) {
      this.projects.push({
        title: title,
        isComplete: false,
        isGoing: false,
        description: description,
      });
      this.showProjects = true;
      this.showAddProject = false;
    },
    deleteProject(title) {
      const index = this.projects.findIndex(
          (project) => project.title === title
      );
      this.projects.splice(index, 1);
      this.completedProjects = this.projects.filter((t) => {
        return t.isComplete !== false;
      });
      this.isGoingProjects = this.projects.filter((t) => {
        return t.isComplete !== true;
      });
    },
    completeProject(title) {
      const p = this.projects.find((project) => project.title === title);
      p.isComplete = !p.isComplete;
      this.completedProjects = this.projects.filter((t) => {
        return t.isComplete !== false;
      });
      this.isGoingProjects = this.projects.filter((t) => {
        return t.isComplete !== true;
      });
    },
  },
};
</script>

<style>




* {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  list-style: none;
  text-decoration: none;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Montserrat', sans-serif;
  background: white;
  color: var(--color-light);
  line-height: 1.7;
}



h1 {
  font-size: 2rem;
  color: var(--color-white);
  font-family: 'Montserrat', sans-serif;
  border: 1px solid #d02718


}

p{
  font-size: 1.1rem;
  font-family: 'Montserrat', sans-serif;
  color: white;
}

h2 {
  font-size: 1.3em;
  color: white;

}

a {
  color: black;
}



img{
  display: block;
  object-fit: cover;
  width: 100%;
}


</style>