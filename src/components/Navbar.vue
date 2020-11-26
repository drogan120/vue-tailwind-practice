<template>
    <nav class="bg-blue-400 text-gray-100 px-6 py-4 border-b">
        <div class="flex justify-between mb-3">
            <a href="/" class="text-lg font-medium">Drogan120</a>
            <button>
                <svg
                    class="w-6 h-6"
                    xlmns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24 "
                    stroke="currentColor"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M4 6h16M4 12h16m-7 6h7"
                    />
                </svg>
            </button>
        </div>
        <div
            class="flex items-center justify-between text-sm py-4 border-t border-gray-100"
        >
            <div class="flex flex-col lg:flex-row item-center">
                <router-link
                    to="/"
                    class="block py-4 px-4 text-gray-300 hover:text-gray-100"
                    >Home</router-link
                >
                <router-link
                    to="/about"
                    class="block py-4 px-4 text-gray-300 hover:text-gray-100"
                    >About</router-link
                >
            </div>
        </div>
    </nav>
</template>
