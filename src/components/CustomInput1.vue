<template>
  <input type="text" :value="searchText" @input="onInput" />
</template>

<script lang="ts">
import { Component, Emit, Vue } from "vue-property-decorator";

@Component
export default class CustomInput1 extends Vue {
  private readonly searchText = "";

  @Emit("input")
  private onInput(event: any) {
    return event.target.value;
  }
}
</script>

<style scoped></style>
