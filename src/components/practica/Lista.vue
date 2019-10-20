<template>
  <div class="seccion">
    <div class="atributo" v-for="(item, index) in tareas" :key="index">
      <span>{{ item }}</span>
      <div class="tarea">
        <button :disabled="disabled" @click="EditarTarea(index)">✏</button>
        <button :disabled="disabled" @click="EliminarTarea(index)">✖</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tareas: {
      required: true,
      type: Array
    },
    disabled: {
      type: Boolean
    }
  },
  methods: {
    EliminarTarea(index) {
      this.$emit("onEliminarTarea", index);
    },
    EditarTarea(index) {
      this.$emit("onEditarTarea", index);
    }
  }
};
</script>

<style lang="css">
.tarea {
  display: inline;
  margin: 20px;
}
</style>
