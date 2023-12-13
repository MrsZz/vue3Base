<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{ count1 }}</p>
  </div>
  <div>
    <button type="button" @click="getNumber">数字会累加</button>
    <button type="button" @click='getNumberCount'>数字会累加</button>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import { toRaw } from '@vue/reactivity'

@Options({
  props: {
    msg: String
  },
  data () {
    return {
      count: '12'
    }
  }
})
export default class HelloWorld extends Vue {
  msg!: string
  count1 = 0;
  data () {
    return {
      conut: '12324'
    }
  }

  getNumberCount () {
    console.log(this)
    const Obj = {
      name: 'zhangsan',
      age: 19
    }
    const custProxy = new Proxy(Obj, {
      get(target: any, propertyKey:any) {
        return target[propertyKey]
      }
    });
    console.log(custProxy)
    console.log(toRaw(custProxy));
    console.log(JSON.parse(JSON.stringify(custProxy)));
    
    console.log(toRaw(this));
    console.log(JSON.parse(JSON.stringify(this)));
    
  }

  getNumber () {
    // this.count = 12 + count
    console.log(this)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
