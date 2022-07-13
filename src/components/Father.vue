<template>
  <Son prop1="问渠那得清如许" @message="showMessage"></Son>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Son from "./Son.vue";

@Component({
  components: {
    Son,
  },
})
export default class Father extends Vue {
  private showMessage(message: string): void {
    alert("father show message: " + message);
  }
}
</script>
