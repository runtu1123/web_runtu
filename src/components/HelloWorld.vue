<template>
  <div class="hello">
    <p>{{msg}}</p>
    <button @click="handleclick()">{{runtu}}</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "当前点击次数",
      runtu: "击",
      jz: true
    };
  },
  methods: {
    handleclick() {
      if (this.jz) {
        this.jz = false;
        this.msg++;
        setTimeout(() => {
          this.jz = true;
        }, 5000);
      }else{
        console.log("时间未到")
      }
    }
  },
  mounted() {
    var url = "https://httpbin.org/delay";
    this.axios.get("https://httpbin.org/delay/0?inc=1").then(result => {
      this.msg = result.data.args.inc;
    });
  }
};
</script>

<style scoped>
button {
  width: 300px;
  height: 200px;
  font-size: 50px;
}
</style>
