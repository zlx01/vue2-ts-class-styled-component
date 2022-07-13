<template>
  <input type="text" v-model="syncedName" />
</template>

<script lang="ts">
import { Component, PropSync, Vue } from "vue-property-decorator";

@Component
export default class CustomInput3 extends Vue {
  @PropSync("searchText", { type: String })
  syncedName!: string;
}
</script>

<style scoped></style>
