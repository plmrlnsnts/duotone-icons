<template>
    <div class="min-h-screen bg-white">
        <header class="py-16 sm:py-24 lg:py-32" :class="colors[color].gradient">
            <div class="sm:text-center w-full max-w-2xl mx-auto px-6 space-y-8">
                <h1 class="text-4xl sm:text-5xl md:text-7xl font-black tracking-tight"><span class="text-white/75">duo</span><span class="text-white/95">tone</span> <span class="font-light text-white">icons</span></h1>
                <p class="sm:text-xl font-medium text-white">688 free, sexy af, two-tone SVG icons. <br/>Icons from <a href="https://preview.keenthemes.com/start/documentation/general/icons/duotone.html" target="_blank" rel="noopener noreferrer" class="hover:text-white hover:underline">@keenthemes</a>. Viewer by <a href="https://twitter.com/plmrlnsnts" target="_blank" rel="noopener noreferrer" class="hover:text-white hover:underline">@plmrlnsnts</a>.</p>
            </div>
        </header>
        <main>
            <nav class="h-16 sticky top-0 bg-white border-b flex z-10">
                <SearchInput @search="filter" class="flex-1" />
                <ColorSwitcher v-model:color="color" :colors="colors" />
            </nav>
            <div class="grid grid-cols-3 sm:grid-cols-4 md:grid-cols-5 lg:grid-cols-6 xl:grid-cols-8 gap-px">
                <DuotoneIconButton v-for="icon in icons" :key="`icon-${icon.name}-${icon.tags}`" :icon="icon" :color="colors[color]" />
            </div>
        </main>
    </div>
</template>

<script>
import ColorSwitcher from './components/ColorSwitcher.vue'
import DuotoneIconButton from './components/DuotoneIconButton.vue'
import DuotoneIcons from './icons.json'
import SearchInput from './components/SearchInput.vue'

export default {
    components: {
        ColorSwitcher,
        DuotoneIconButton,
        SearchInput,
    },

    data: () => ({
        icons: DuotoneIcons,
        color: 'pink',
        colors: {
            pink: {
                gradient: 'bg-gradient-to-r from-pink-500 to-pink-700',
                bgPrimary: 'bg-pink-600',
                bgSecondary: 'bg-pink-400',
                textPrimary: 'text-pink-600',
                textSecondary: 'text-pink-400',
            },
            purple: {
                gradient: 'bg-gradient-to-r from-purple-500 to-purple-700',
                bgPrimary: 'bg-purple-600',
                bgSecondary: 'bg-purple-400',
                textPrimary: 'text-purple-600',
                textSecondary: 'text-purple-400',
            },
            blue: {
                gradient: 'bg-gradient-to-r from-blue-500 to-blue-700',
                bgPrimary: 'bg-blue-600',
                bgSecondary: 'bg-blue-400',
                textPrimary: 'text-blue-600',
                textSecondary: 'text-blue-400',
            },
            green: {
                gradient: 'bg-gradient-to-r from-green-500 to-green-700',
                bgPrimary: 'bg-green-600',
                bgSecondary: 'bg-green-400',
                textPrimary: 'text-green-600',
                textSecondary: 'text-green-400',
            },
            yellow: {
                gradient: 'bg-gradient-to-r from-yellow-500 to-yellow-700',
                bgPrimary: 'bg-yellow-600',
                bgSecondary: 'bg-yellow-400',
                textPrimary: 'text-yellow-600',
                textSecondary: 'text-yellow-400',
            },
        },
    }),

    methods: {
        filter(term) {
            this.icons = DuotoneIcons.filter(({ name, tags }) => {
                return name.includes(term) || tags.includes(term)
            })
        },
    },
}
</script>
