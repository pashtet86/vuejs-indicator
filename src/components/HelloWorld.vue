<template>
  <div class="hello">
    <h1>Indicator component demo</h1>
    <h2>basic usage (with tooltip on hover)</h2>
    <ul>
      <li><indicator status="past" /> <span>Vue.js 1.2</span></li>
      <li><indicator status="active" /> <span>Vue.js 2.3</span></li>
      <li><indicator status="draft" /> <span>Vue.js 3.0</span></li>
    </ul>
    <h2>show status text mode (without tooltip)</h2>
    <ul>
      <li><indicator status="inactive" showtext /></li>
      <li><indicator status="active" showtext /></li>
      <li><indicator status="pending" showtext /></li>
      <li><indicator status="deleted" showtext /></li>
    </ul>
    <h2>sizing</h2>
    <ul>
      <li><indicator status="active" :size="8" /> <span>Item 1</span></li>
      <li><indicator status="pending" :size="15" /> <span>Item 2</span></li>
      <li><indicator status="depricated" :size="20" /> <span>Item 3</span></li>
    </ul>
  </div>
</template>

<script>
import Indicator from "./Indicator";

export default {
  name: "HelloWorld",
  components: {
    Indicator
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
  margin-top: 50px;
  margin-bottom: 0;
}
ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
li {
  display: inline-flex;
  align-items: center;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
