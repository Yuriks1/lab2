<template>
  <form @submit.prevent="submitForm">
    <label for="title">Title</label>
    <input name="title" id="title" v-model="title" required>

    <label for="description">Description:</label>
    <textarea name="description" id="description" v-model="description" rows="5" required></textarea>
    <div v-if="error" class="error">{{  error  }}</div>
    <div class="submit">
      <button>Add a Project</button>
    </div>
  </form>

</template>

<script>
export default {
  data() {
    return {
      title: '',
      description: '',
      error: '',
    }
  },
  methods: {
    submitForm() {
      this.error = (this.title && this.description) ? '' : 'Please enter Title and Description'
      if (this.error) {
        return;
      }
      this.$emit("add", this.title, this.description);
    }
  }

}
</script>

<style scoped>

nav button {

  box-shadow:inset 0 1px 0 0 #f5978e;
  background: #f24537 linear-gradient(to bottom, #f24537 5%, #c62d1f 100%);
  border-radius:6px;
  border:1px solid #d02718;
  text-decoration: none;
  margin: 1rem;
  font-size:15px;
  font-weight:bold;
  padding:6px 24px;
  text-shadow:0 1px 0 #810e05;
}

nav button:hover {
  cursor: pointer;
  color: white;
}


form {
  position: relative;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 15px;
}

label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 1em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input,
textarea {
  display: block;
  padding: 10px 6px;
  box-sizing: border-box;
  width: 100%;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}

button {
  background-color:red;
  border: 0;
  padding: 10px 15px;
  margin-top: 10px;
  color: white;
  border-radius: 30px;
  font-size: 15px;
}

button:hover {
  background: black;
}

.submit {
  text-align: center;
  margin-top: 50px;
}

</style>