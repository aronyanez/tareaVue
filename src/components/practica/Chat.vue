<template>
  <div class="principal">
    <div>Chat</div>
    <div class="emojis seccion">
      <emoji
        @onRecibirEmoji="mostrarEmoji"
        :caracter="item.caracter"
        v-for="item  in emojis"
        :key="item.id"
      />
    </div>
    <div class="seccion">
      <input @keyup.enter="enviarTarea" v-model="texto" type="text" />
      <button @click="enviarTarea">🚀</button>
    </div>

    <lista
      :tareas="tareas"
      @onEliminarTarea="eliminarTarea"
      @onEditarTarea="editarTarea"
      v-if="tareas != []"
      :disabled="editando"
    />
  </div>
</template>

<script>
import Emoji from "./Emoji.vue";
import Lista from "./Lista.vue";

export default {
  components: { Emoji, Lista },
  data() {
    return {
      //https://www.alt-codes.net/smiley_alt_codes.php
      //https://www.quackit.com/character_sets/emoji/emoji_v3.0/emoji_icons_food_and_drink.cfm
      emojis: [
        { id: 1, caracter: "🥑" },
        { id: 2, caracter: "🍞" },
        { id: 3, caracter: "🍻" },
        { id: 4, caracter: "🍿" },
        { id: 5, caracter: "🍣" },
        { id: 6, caracter: "🤠" },
        { id: 7, caracter: "😋" },
        { id: 8, caracter: "😢" },
        { id: 9, caracter: "❤️" },
        { id: 10, caracter: "👍" }
      ],
      texto: "",
      tareas: [],
      editando: false,
      indexEditando: ""
    };
  },
  methods: {
    mostrarEmoji(emoji) {
      this.texto += emoji;
    },
    eliminarTarea(index) {
      this.tareas.splice(index, 1);
    },
    editarTarea(index) {
      let tarea = this.tareas[index];
      this.indexEditando = index;
      this.texto = tarea;
      this.editando = true;
      console.log(tarea);
    },
    enviarTarea() {
      if (this.editando == true) {
        this.tareas[this.indexEditando] = this.texto;
        this.editando = false;
      } else {
        this.tareas.push(this.texto);
      }
      this.texto = "";
    }
  }
};
</script>

<style>
button {
  margin: 10px;
  width: 60px;
  height: 60px;
  cursor: pointer;
  font-size: 30px;
  border-style: solid;
  border-width: 3px;
  border-color: #3090c7;
  border-radius: 5px;
}

button:disabled {
  background: grey;
}

.emojis {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>

