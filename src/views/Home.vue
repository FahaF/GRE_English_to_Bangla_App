<template>
    <div class="home">
        <div class="card" >
          <img v-if="logo" :src="logo.url" alt="logo">
        </div>
        <div class="head">
            <h1>Welcome to GRE Vocabulary App</h1>
        </div>
        <div class="content">
          <EnterButton></EnterButton>
        </div>
    </div>
</template>

<style scoped lang="scss">
   .home {
      padding: 10px;
      padding: 10px;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      .card {
        padding: 15px;
        min-height: 200px;
        width: 300px;
        align-self: center;
        img {
          width: 70%;
        }
        @media (min-width: 768px)  {
            img {
              width: 100%;
            }
          min-height: 320px;  
          width: 400px;
          padding: 35px;
          }
      }
       .head  {
          padding: 12px;
       }
       .content {
            padding: 25px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            justify-content: center;

       }
   }
</style>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import EnterButton from '@/components/EnterButton.vue';

@Component({
  components: {
    EnterButton,
  },
})
export default class Home extends Vue {
  get logo() {
    return this.$store.getters.logo;
  }

}
</script>
