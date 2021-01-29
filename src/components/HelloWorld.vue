<template>
  <div class="hello">
    <h1 @click="getMsg">{{ msg }}</h1>
    <div v-for="(item, index) in person" :key="index">
      {{item.value}}
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
    msg: String
  }
})
export default class HelloWorld extends Vue {
  msg!: string ;

  get computedMsg(){
    return 'computed ' + this.msg
  }

  getMsg (): void{
    console.log(this.computedMsg)
  }

  setup() {
    const person: Array<string> = ['小明', '刘莹', '小红']
    const nums: Array<number> = [11, 12, 13]
    const sex: Boolean[] = [true, false, false]
    return {
      person,
      nums,
      sex
    }
  }

  mounted() {
    this.getMsg()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
