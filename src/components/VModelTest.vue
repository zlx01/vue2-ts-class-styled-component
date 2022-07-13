<template>
  <input type="text" v-model="name" />
</template>

<script lang="ts">
import { Component, VModel, Vue } from "vue-property-decorator";

@Component
export default class VModelTest extends Vue {
  @VModel({ type: String })
  name!: string;
}
</script>

<style scoped></style>
