<script lang="ts" setup>
import { ref } from "#imports";
import Transitioned from "~/components/design/Transitioned.vue";

const props = withDefaults(
  defineProps<{
    delay?: number;
  }>(),
  {
    delay: 300,
  }
);

function delay(time: number) {
  return new Promise((resolve) => setTimeout(resolve, time));
}

const show = ref(false);
delay(props.delay).then(() => {
  show.value = true;
});
</script>

<template>
  <Transitioned :show="show">
    <slot />
  </Transitioned>
</template>
