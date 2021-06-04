<template>
  <v-app>
    <v-main>
      <Home/>
    </v-main>
  </v-app>
</template>

<script>
import Home from './components/Home';

export default {
  name: 'App',

  components: {
    Home,
  },

  data: () => ({
    //
  }),
};
</script>

<style>
/* width */
::-webkit-scrollbar {
  width: 7px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #121212;
}

/* Handle */
::-webkit-scrollbar-thumb {
  border-radius: 10px;
  background: #424242;
  /* display: none; */
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: rgb(104, 104, 104);
}
</style>