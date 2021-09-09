<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ messgae }}</h2>
    <ul v-for="(user, index) in userList" :key="index">
      <li>{{ user }}</li>
    </ul>
    <button @click="resetList">reset list</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  @Prop({ type: Number, default: 0 }) readonly age!: number;
  @Prop({ type: Array, default: [] }) readonly userList!: string[];
  @Prop({ type: Boolean, default: false }) readonly isMultiSelect!: boolean;

  get messgae(): string {
    const id = this.$attrs.id;
    return `user count is ${this.userList.length}, and id is ${id || "NONE"}`;
  }

  resetList(): void {
    this.$emit("reset-list");
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
