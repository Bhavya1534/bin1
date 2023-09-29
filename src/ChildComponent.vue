<template>
  <div>
    <slot></slot>
    <button @click="emitCustomEvent">Trigger Event</button>
  </div>
</template>

<script>
export default {
  props: ['prop1'],
  methods: {
    emitCustomEvent() {
      this.$emit('custom-event', { message: 'Custom event data' });
    },
  },
};
</script>
