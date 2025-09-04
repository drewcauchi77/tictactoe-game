<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';

defineProps({
   game: Object
});
</script>

<template>
    <AppLayout>
        <h1>Testing</h1>

        {{ game }}
    </AppLayout>
</template>
