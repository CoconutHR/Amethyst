<script setup lang="ts">
import type { Placement } from "@floating-ui/core";

import BasePopover from "@/components/BasePopover.vue";
defineProps<{
	text?: string
	placement?: Placement
	borderless?: boolean
}>();
</script>

<template>
  <base-popover
    open-on-hover
    :placement="placement"
    :arrow="true"
    class="tooltip"
    :class="borderless ? '' : ' border-solid border-1 border-surface-600 bg-surface-800 p-2' "
  >
    <slot />
    <template #content>
      <p class=" text-text-title whitespace-pre text-center text-13px">
        {{ text }}
      </p>
      <slot name="content" />
    </template>
  </base-popover>
</template>

<style lang="postcss">
.tooltip {
  @apply z-200;
}
.tooltip.popover {
  @apply text-text-title shadow-xl;
}

</style>