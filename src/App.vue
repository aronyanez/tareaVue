<template>
  <chat />
</template>

<script>
import Chat from '@/components/practica/Chat.vue'

export default {
  components: { Chat }
}
</script>

<style>

html {
  font-size: 62.5% !important; /* 10px / 16px = 0.625 */
}

.principal {
  background-color:#3090C7;
  padding: 10px;
  color: white;
  border-radius: 5px;
  width: 800px;
  font-size: 3rem;
  text-align: center;
}

button:focus
{
  outline: 0;
}

input[type='text'] {
  border-radius: 5px;
  font-size: 2.2rem;
  width: 80%;
  line-height: 4rem;
  padding: 3px;
}

.seccion {
  font-size: 2.4rem;
  color: #202020;
  background-color: #e9e9e9;
  border-radius: 5px;
  margin: 10px;
  padding: 10px;
}

.atributo {
  margin: 10px;
}

</style>
