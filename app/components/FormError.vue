<script setup>

const props = defineProps(["errors"]);
</script>

<template>
  <div class="space-y-2" :class="{ error: props.errors?.length }">
    <slot />
    <div class="input-errors" v-for="error in props.errors" :key="error.$uid">
      <div class="text-red-500 error-msg">{{ error.$message }}</div>
    </div>
  </div>
</template>
