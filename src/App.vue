<template>
  <v-app>
    <v-toolbar app>
    </v-toolbar>

    <v-content>

      <div class="wrapper">
      <div class="cont">
        <div class="sideLeft"></div> 
        <div class="main"><Main/></div>
        <div class="sideRight"></div> 
      </div>
      </div>

    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Main from './components/Main'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Main
  },
  data () {
    return {
      //
    }
  }
}
</script>


<style lang="scss" scoped>

.wrapper{
  justify-content: center;
  display: flex;
}

  .cont{
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: center;
    width:90%;

      .sideLeft, .sideRight{
        width:10%;
        margin-top: 50px;
        // background: red;
      }

      .main{
        width: 50%;
        margin: 50px 20px 0 20px;
        // background: lightblue;
        min-height: 500px;
      }
  }
</style>
