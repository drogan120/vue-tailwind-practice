<template>
    <link
        rel="stylesheet"
        href="http://localhost/source/fontawesome-5.11.2/css/all.css"
    />
    <div class="flex container h-screen w-full">
        <!-- Side navbar -->
        <div
            class="lg:w-1/5 border-r border-t-lighter px-2 lg:px-6
             py-2 flex flex-col justify-between"
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
                    <p class="text-lg font-semibold text-left hidden lg:block">
                        {{ tab.title }}
                    </p>
                </button>
            </div>
            <button
                class="text-t-lighter bg-t-blue rounded-full font-semibold
                 focus:outline-none h-12 w-12 lg:h-auto lg:w-full p-3 hover:bg-t-dark-blue mb-40"
            >
                <div><p class="hidden lg:block">Tweet</p></div>
                <div class="sm:block lg:hidden">
                    <i class="fas fa-plus"></i>
                </div>
            </button>
            <div class="lg:w-full relative">
                <button
                    @click="dropdown = true"
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
                    <i
                        class="hidden lg:block fas fa-angle-down ml-auto text-lg"
                    ></i>
                </button>
                <div
                    v-if="dropdown === true"
                    class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md
                    border-t-lightest bg-white mb-16"
                >
                    <button
                        @click="dropdown = false"
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
                    <button
                        @click="dropdown = false"
                        class="w-full text-left hover:bg-t-lightest border-t
                        border-t-lighter p-3 text-sm"
                    >
                        Add an existing account
                    </button>
                    <button
                        @click="dropdown = false"
                        class="w-full text-left hover:bg-t-lightest border-t
                        border-t-lighter p-3 text-sm"
                    >
                        Log out @drogan120
                    </button>
                </div>
            </div>
        </div>
        <div class="w-1/2 h-full"></div>
        <div
            class=" md:block hidden w-1/3 h-full border-l
            border-t-lighter py-2 px-6 overflow-y-scroll relative"
        >
            <input
                type="text"
                class="pl-12 rounded-full w-full p-2 bg-t-lighter text-sm text-t-light mb-4"
                placeholder="Search Twitter"
            />
            <i
                class="fas fa-search absolute left-0 top-0 mt-5 ml-12 text-sm text-t-light"
            ></i>
            <div class="w-full rounded-lg bg-t-lightest p-3 ">
                <div class="flex items-center justify-between p-3">
                    <p class="text-lg font-bold"> Trends for you</p>
                    <i class="fas fa-cogs text-lg text-t-blue"></i>
                </div>
                <button v-for="trend in trending" :key="trend.top"
                class="w-full flex justify-between hover:bg-lighter p-3 border-t border-t-lighter">
                  <div>
                    <p class="text-sm text-left leading-tight text-t-dark">{{ trend.top }}</p>
                    <p class="font-bold text-left leading-tight">{{ trend.title }}</p>
                    <p class=" text-left leading-tight">{{ trend.bottom }}</p>
                  </div>
                  <i class="fas fa-angle-down text-lg text-t-dark"></i>
                </button>
                <button
                class="p-3 w-full hover:bg-t-lighter
                text-left text-t-blue border-t border-t-lighter">
                  Show More
                </button>
            </div>
            <div class="w-full rounded-lg bg-t-lightest my-4">
                <div class=" p-3">
                    <p class="text-lg font-bold"> Who to follow</p>
                </div>
                <button v-for="friend in friends" :key="friend.handler"
                class="w-full flex hover:bg-lighter p-3 border-t border-t-lighter">
                   <img
                            :src="`../assets/ ${ friend.img }`"
                            alt=""
                            class="w-12 h-12 rounded-full border border-t-lighter"
                        />
                        <div class="ml-4">
                            <p class="text-sm font-bold leading-tight">
                                {{ friend.name }}
                            </p>
                            <p class="text-sm leading-tight">{{ friend.handle }}</p>
                        </div>
                    <button
                     class="ml-auto text-sm text-t-blue py-2 px-4
                      rounded-full border-2 border-t-blue">
                        Follow
                     </button>
                </button>
                <button
                class="p-3 w-full hover:bg-t-lighter
                text-left text-t-blue border-t border-t-lighter">
                  Show More
                </button>
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
      trending: [
        { top: 'lorem', title: 'lorem ipsum', bottom: 'Trending with : Lorem' },
        { top: 'lorem', title: 'lorem ipsum', bottom: 'Trending with : Lorem' },
        { top: 'lorem', title: 'lorem ipsum', bottom: 'Trending with : Lorem' },
        { top: 'lorem', title: 'lorem ipsum', bottom: 'Trending with : Lorem' },
        { top: 'lorem', title: 'lorem ipsum', bottom: 'Trending with : Lorem' },
      ],
      friends: [
        { img: 'logo.png', name: 'lorem ipsum', handle: '@lortem' },
        { img: 'logo.png', name: 'lorem ipsum', handle: '@lortem' },
        { img: 'logo.png', name: 'lorem ipsum', handle: '@lortem' },
        { img: 'logo.png', name: 'lorem ipsum', handle: '@lortem' },
      ],
    };
  },
};
</script>
