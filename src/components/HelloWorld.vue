<template>
  <div class="hello">
    <div>{{ show }} {{ total.txt }}</div>
    <h1>{{ msg }}</h1>
    <label v-text="show"></label>
    <div>
    <button @click="update()">AAAA</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      total: {
        txt:100
      },
    }
  },
  computed:{
    show(){
      return this.total.txt;
    }
  },
  watch:{
    total: {
      handler(n){
        console.log('watch-->',n.txt);
      },
      deep:true
    }
  },
  methods: {
    update(){
      this.$forceUpdate();
    }
  },
  created () {
    console.log(this.total.txt)
    setInterval(() => {
      console.log('timer', this.total.txt)
      this.total.txt += 1
    }, 3000)

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
