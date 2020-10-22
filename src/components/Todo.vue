<template>
  <div>
    <h1 :class="{ completed }" v-if="!isEditing">{{ todoString }}</h1>
    <input @blur="endEditing()" v-else v-model="newTodoString" type="text" />
    <button @click="$emit('on-delete')" :class="{ completed }" class="main">
      Delete
    </button>
    <button @click="startEditing()" :class="{ completed }" class="main">
      Edit
    </button>
  </div>
</template>

<script>
export default {
  props: {
    todoString: String,
    completed: Boolean,
  },
  data() {
    return {
      isEditing: false,
      newTodoString: "",
    };
  },
  methods: {
    startEditing() {
      if (!this.isEditing) {
        this.newTodoString = this.todoString;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing() {
      this.isEditing = false;
      this.$emit("on-edit", this.newTodoString);
    },
  },
};
</script>

<style></style>
