<script>
  import { store } from './store';
  import AppHeader from './components/AppHeader.vue';
  import AppMain from './components/AppMain.vue';

export default{
  components:{
    AppHeader,
    AppMain,
  },
  data() {
    return {
      store,
    }
  },

}

</script>

<template>
  <AppHeader/>
  <AppMain />
</template>

<style lang="scss">
  @use './style/general.scss' as*;
  @use './style/partial/variables' as*;
  
</style>
