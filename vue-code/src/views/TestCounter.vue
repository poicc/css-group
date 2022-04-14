<template>
  <div class="test-counter">
    <Counter />
  </div>
</template>

<script>
import Counter from "../components/couter/Couter.vue";
import { defineComponent } from "vue";
export default defineComponent({
  name: "TestCounter",
  components: {
    Counter,
  },
});
</script>