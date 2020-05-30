<template>
  <div>
    <form @submit.prevent="addTodo">
      <!-- .prevent -> prevents default form submission -->
      <input type="text" v-model="title" name="title" placeholder="Add Todo" />
      <input type="submit" class="btn" value="Submit" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        //id: Math.floor((Math.random() * 10) + 1), (json placeholder provides an id by default)
        title: this.title,
        completed: false
      };
      //Send up to the parent
      this.$emit("add-todo", newTodo);

      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>