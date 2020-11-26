<template>
    <link
        rel="stylesheet"
        href="http://localhost/source/fontawesome-5.11.2/css/all.css"
    />
    <div class="flex container h-screen w-full">
        <!-- Side navbar -->
        <div class="w-1/5 border-r border-t-lighter px-8 py-2
        flex flex-col justify-between">
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
                    <p class=" text-lg font-semibold  text-left">{{ tab.title }}</p>
                </button>
            </div>
            <button
                class="text-t-lighter bg-t-blue rounded-full font-semibold
                 focus:outline-none w-full p-3 hover:bg-t-dark-blue"
            >
                Tweeet
            </button>

            <button class="flex items-center">
                <img
                    src="../assets/logo.png"
                    alt=""
                    class="w-12 h-12 rounded-full border border-t-lighter"
                />
                <div class="ml-4">
                    <p class="text-sm font-bold">Drogan120</p>
                    <p class="text-sm">@drogan120</p>
                </div>
                <i class="fas fa-angle-down ml-auto text-lg"></i>
            </button>
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
        { icon: 'fas fa-elipsis-h', title: 'More', id: 'more' },
      ],
    };
  },
};
</script>
