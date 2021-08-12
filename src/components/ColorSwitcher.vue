<template>
    <div class="hidden sm:flex items-center justify-center space-x-2 px-6">
        <button @click="$emit('update:color', c)" v-for="c in Object.keys(colors)" :key="`color-switcher-${c}`" class="flex w-8 h-8 border-4 border-white shadow rounded-full overflow-hidden translate rotate-45 transform active:scale-95" :class="{ 'opacity-50 hover:opacity-100' : c !== color }">
            <span class="h-full w-1/2" :class="colors[c].bgPrimary"></span>
            <span class="h-full w-1/2" :class="colors[c].bgSecondary"></span>
        </button>
    </div>
</template>

<script>
export default {
    props: {
        color: String,
        colors: Object,
    },

    emits: ['update:color'],
}
</script>
