<template>
  <v-app>
    <v-main>
      <v-container fluid class="text-center">
        <h2 class="text-h1 font-weight-black mt-3">The cat 🐱</h2>
        <p class="pa-2">귀여운 고양이가 보고싶을때 힐링하러오는 고양이 휴게소...</p>
        <router-view></router-view>
      </v-container>
    </v-main>
  </v-app>      
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    value: 'home' ,
    
    }),
};
</script>

<style >
body {
  background-color: aliceblue;
}

.v-item-group.v-bottom-navigation {
  align-items: center;
}

.v-application {
  max-width: 700px;
  margin: 20px auto;
  border-radius: 15px;
}

</style>