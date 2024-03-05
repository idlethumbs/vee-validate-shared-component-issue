<template>
    <ErrorMessage :name="name" />
</template>

<script lang="ts" setup>
import { ErrorMessage } from 'vee-validate';

defineProps({
  name: String,
});
</script>