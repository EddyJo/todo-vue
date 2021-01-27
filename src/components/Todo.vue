<template>
    <div>
      <input type="checkbox" :checked="todo.checked"
        @change="toggleCheckBox">
      <span class="ml-3">
        {{ todo.text }}
      </span>
    </div>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    },
    methods : {
      toggleCheckBox(e) {
        console.log("hi");
        this.$emit('toggle-checkbox', {
          id: this.todo.id,
          checked: e.target.checked
        })
      }
    }
}
</script>

<style>

</style>