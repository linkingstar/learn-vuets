<template>
  <div class="home">
    <hello-world
      msg="message from home"
      :userList="userList"
      id="Hello World"
      @reset-list="cleanList"
    />
    <button @click="addData">add data</button>
    <button @click="removeData">remove data</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

@Component({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {
  userList = ["Abe", "Back", "Count"];

  addData(): void {
    this.userList.push("Mike");
  }

  removeData(): void {
    this.userList.splice(0, 1);
  }

  cleanList(): void {
    this.userList = [];
  }
}
</script>
<style lang="scss" scoped>
.home {
  button + button {
    margin-left: 12px;
  }
}
</style>
