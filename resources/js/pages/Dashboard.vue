<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { dashboard } from '@/routes';
import { type BreadcrumbItem } from '@/types';
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    games: Object
});

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Dashboard',
        href: dashboard().url,
    },
];
</script>

<template>
    <Head title="Dashboard" />

    <AppLayout :breadcrumbs="breadcrumbs">
        <div class="flex h-full flex-1 flex-col gap-4 overflow-x-auto rounded-xl p-4">
            <Link :href="route('games.store')" method="post" as="button">Create Game</Link>

            <ul class="divide-y mt-6">
                <li v-for="game in games.data" :key="game.id" class="px-2 py-1.5 flex justify-between items-center">
                    <span>{{ game.player_one.name }}</span>
                    <Link :href="route('games.join', game)" method="post" as="button" class="hover:bg-gray-100 transition-colors p-2 rounded">Join Game</Link>
                </li>
            </ul>
        </div>
    </AppLayout>
</template>
