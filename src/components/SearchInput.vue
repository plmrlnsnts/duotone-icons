<template>
    <div class="relative h-full">
        <input @input="search($event.target.value)" type="text" class="pl-12 sm:pl-16 block h-full w-full bg-transparent text-lg font-medium focus:outline-none" placeholder="Search icons">
        <div class="absolute inset-y-0 flex items-center px-4 sm:px-6">
            <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" class="w-6 h-6" viewBox="0 0 24 24" version="1.1">
                <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                    <path d="M14.2928932,16.7071068 C13.9023689,16.3165825 13.9023689,15.6834175 14.2928932,15.2928932 C14.6834175,14.9023689 15.3165825,14.9023689 15.7071068,15.2928932 L19.7071068,19.2928932 C20.0976311,19.6834175 20.0976311,20.3165825 19.7071068,20.7071068 C19.3165825,21.0976311 18.6834175,21.0976311 18.2928932,20.7071068 L14.2928932,16.7071068 Z" fill="currentColor" class="text-gray-400" fill-rule="nonzero"></path>
                    <path d="M11,16 C13.7614237,16 16,13.7614237 16,11 C16,8.23857625 13.7614237,6 11,6 C8.23857625,6 6,8.23857625 6,11 C6,13.7614237 8.23857625,16 11,16 Z M11,18 C7.13400675,18 4,14.8659932 4,11 C4,7.13400675 7.13400675,4 11,4 C14.8659932,4 18,7.13400675 18,11 C18,14.8659932 14.8659932,18 11,18 Z" fill="currentColor" class="text-gray-600" fill-rule="nonzero"></path>
                </g>
            </svg>
        </div>
    </div>
</template>

<script>
import { debounce } from 'lodash'

export default {
    emits: ['search'],

    methods: {
        search: debounce(function (term) {
            term = term.trim().toLowerCase()

            this.$emit('search', term)
        }, 300),
    },
}
</script>
