<template>
    <link
        rel="stylesheet"
        href="http://localhost/source/fontawesome-5.11.2/css/all.css"
    />
    <div class="flex container h-screen w-full">
        <!-- Side navbar -->
        <div
            class="lg:w-1/5 border-r border-t-lighter px-2 lg:px-6 py-2 flex flex-col
             justify-between"
        >
            <button
                class="h-12 w-12 hover:bg-t-light-blue text-3xl rounded-full text-t-blue"
            >
                <i class="fab fa-twitter"></i>
            </button>
            <div>
                <button
                    v-for="tab in tabs"
                    v-bind:key="`${tab.id}`"
                    @click="id = tab.id"
                    :class="`focus:outline-none hover:text-t-blue flex items-center py-2 px-4
                    hover:bg-t-light-blue rounded-full mr-auto`"
                >
                    <i :class="`${tab.icon} text-2xl mr-4`"></i>
                    <p class="text-lg font-semibold text-left hidden lg:block ">
                        {{ tab.title }}
                    </p>
                </button>
            </div>
            <button
                class="text-t-lighter bg-t-blue rounded-full font-semibold
                focus:outline-none h-12 w-12 lg:h-auto lg:w-full p-3 hover:bg-t-dark-blue mb-40"
            >
                <p class="hidden lg:block">Tweeet</p>
                <i class="fas fa-plus sm:block lg:hidden"></i>
            </button>
            <div class="lg:w-full relative">
                <button @click="dropdown = true "
                    class="flex items-center w-full hover:bg-t-light-blue
                    rounded-full p-2 focus:outline-none"
                >
                    <img
                        src="../assets/logo.png"
                        alt=""
                        class="w-10 h-10 rounded-full border border-t-lighter"
                    />
                    <div class="hidden lg:block ml-4">
                        <p class="text-sm font-bold leading-tight">Drogan120</p>
                        <p class="text-sm leading-tight">@drogan120</p>
                    </div>
                    <i class="hidden lg:block  fas fa-angle-down ml-auto text-lg"></i>
                </button>
                <div v-if="dropdown === true"
                    class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md
                    border-t-lightest bg-white mb-16"
                >
                    <button @click="dropdown=false"
                        class="p-3 flex items-center w-full hover:bg-t-lightest focus:outline-none"
                    >
                        <img
                            src="../assets/logo.png"
                            alt=""
                            class="w-10 h-10 rounded-full border border-t-lighter"
                        />
                        <div class="ml-4">
                            <p class="text-sm font-bold leading-tight">
                                Drogan120
                            </p>
                            <p class="text-sm leading-tight">@drogan120</p>
                        </div>
                        <i class="fas fa-check ml-auto text-t-blue"></i>
                    </button>
                    <button  @click="dropdown=false"
                        class="w-full text-left hover:bg-t-lightest border-t
                        border-t-lighter p-3 text-sm"
                    >
                        Add an existing account
                    </button>
                    <button  @click="dropdown=false"
                        class="w-full text-left hover:bg-t-lightest border-t
                         border-t-lighter p-3 text-sm"
                    >
                        Log out @drogan120
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
  name: 'twitter',
  components: {},
  data() {
    return {
      tabs: [
        { icon: 'fas fa-home', title: 'Home', id: 'home' },
        { icon: 'fas fa-hashtag', title: 'Explore', id: 'explore' },
        { icon: 'fas fa-bell', title: 'Notification', id: 'notification' },
        { icon: 'fas fa-envelope', title: 'Messages', id: 'messages' },
        { icon: 'fas fa-bookmark', title: 'Bookmarks', id: 'bookmarks' },
        { icon: 'fas fa-clipboard-list', title: 'List', id: 'list' },
        { icon: 'fas fa-user', title: 'Profile', id: 'profile' },
        { icon: 'fas fa-ellipsis-h', title: 'More', id: 'more' },
      ],
      id: 'home',
      dropdown: false,
    };
  },
};
</script>
