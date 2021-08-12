<template>
    <button type="button" class="relative block w-full pb-[100%] outline-gray group" @click="copyToClipboard">
        <div class="absolute inset-x-0 bottom-4 text-sm text-center font-medium">{{ icon.name }}</div>
        <div v-if="status === 'idle'" class="absolute inset-0 flex items-center justify-center">
            <div class="w-24 h-24 bg-gray-100 rounded-full transition transform scale-0 group-hover:scale-100"></div>
        </div>
        <div class="absolute inset-0 flex items-center justify-center">
            <transition mode="out-in" enter-active-class="transition ease-out duration-100 transform" enter-from-class="opacity-0 scale-50" enter-to-class="opacity-100 scale-100" leave-active-class="transition ease-in duration-75 transform" leave-from-class="opacity-100 scale-100" leave-to-class="opacity-0 scale-50">
                <div v-if="status === 'idle'" v-html="formattedSvg"></div>
                <div v-else class="bg-gray-900 text-white text-sm font-semibold px-3 py-2 rounded">Copied!</div>
            </transition>
        </div>
    </button>
</template>

<script>
export default {
    props: {
        icon: Object,
        color: Object,
    },

    data: () => ({
        status: 'idle',
    }),

    computed: {
        formattedSvg() {
            return this.icon.svg
                .replaceAll('w-6 h-6', 'w-8 h-8 md:w-10 md:h-10')
                .replaceAll('duotone-primary', this.color.textPrimary)
                .replaceAll('duotone-secondary', this.color.textSecondary)
        },
    },

    methods: {
        copyToClipboard() {
            this.status = 'copied'

            window.navigator.clipboard.writeText(this.icon.svg)

            setTimeout(() => (this.status = 'idle'), 750)
        },
    },
}
</script>
