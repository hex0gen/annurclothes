<script setup>
// // import { ref } from 'vue';
// import { Head, Link, router } from '@inertiajs/vue3';
// import { ref, onMounted, onUnmounted } from "vue";
// import ApplicationLogo from '@/Components/ApplicationLogo.vue';

// const el = ref(null);
// defineProps({
//     title: String,
//     canLogin: Boolean,
//     canRegister: Boolean,
// });

// onMounted(() => {
//     const tham = document.querySelector("#menu-switch");

//     tham.addEventListener('click', () => {
//     tham.classList.toggle('is-active');
//     });    
// });

// // import ApplicationMark from '@/Components/ApplicationMark.vue';
// // import Banner from '@/Components/Banner.vue';
// // import Dropdown from '@/Components/Dropdown.vue';
// // import DropdownLink from '@/Components/DropdownLink.vue';
// // import NavLink from '@/Components/NavLink.vue';
// // import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';


// // const showingNavigationDropdown = ref(false);

// // const switchToTeam = (team) => {
// //     router.put(route('current-team.update'), {
// //         team_id: team.id,
// //     }, {
// //         preserveState: false,
// //     });
// // };

// const logout = () => {
//     router.post(route('logout'));
// };

import { Head, Link, router } from '@inertiajs/vue3';
import { ref, onMounted, onUnmounted } from "vue";
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
    
    const el = ref(null);

    // const observer = new IntersectionObserver((entries, observer) => {
    //   console.log(entries)
    // });

    onMounted(() => {
        const tham = document.querySelector("#menu-switch");

        tham.addEventListener('click', () => {
        tham.classList.toggle('is-active');
        });    
    });


    defineProps({
        title: String,
        canLogin: Boolean,
        canRegister: Boolean,
    });
</script>

<script type="module">
export default {
    name: "modal-component",
    data() {
        return {
            showModal: false
        }
    },
    methods: {
        toggleModal: function () {
            this.showModal = !this.showModal;
        }
    },
}
const logout = () => {
    router.post(route('logout'));
};
</script>

<template>
    <div>
        <Head :title="title" />

        <Banner />

        <div class="flex flex-col h-screen justify-between">
        <nav class="flex flex-row justify-items-center bg-gray-100 py-3 hidden lg:flex">
            <div class="flex basis-1/3 ml-6 py-px">
                <a href="#" class="group text-gray-600 transition duration-300 uppercase pr-5">
                    О нас
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400"></span>
                </a>
                <a href="#" class="group text-gray-600 transition duration-300 uppercase pr-5">
                    Магазин
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400"></span>
                </a>
                <a href="#" class="group text-gray-600 transition duration-300 uppercase pr-5">
                    Lookbook
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400"></span>
                </a>
                <a href="#" class="group text-gray-600 transition duration-300 uppercase pr-5">
                    блог
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400"></span>
                </a>
                <a href="#" class="group text-gray-600 transition duration-300 uppercase">
                    Контакты
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400"></span>
                </a>
            </div>
            
            <a class="block w-full basis-1/3" href="/">
                <ApplicationLogo class="w-auto mx-auto" />
            </a>
    
            <div class="flex justify-end basis-1/3 mr-8 px-px">
                <div class="mx-5 group">
                    <input type="text" class="h-5 border-0 outline-0 bg-gray-100"> <span class="text-gray-500 uppercase">поиск</span>
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-300"></span>
                </div>
                <form method="POST" @submit.prevent="logout">
                    <button type="submit" class="uppercase">Выход</button>
                </form>
                <div v-if="canLogin">
                    <Link v-if="$page.props.auth.user" :href="route('profile')" class="text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500">Профиль</Link>
                    
                    <template v-else>
                        <Link :href="route('login')" class="basis-32 text-gray-500 hover:font-semibold uppercase">Войти</Link>
        
                        <!-- <Link v-if="canRegister" :href="route('register')" class="ms-4 text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500">Регистрация</Link> -->
                    </template>
                </div>
                <div class="flex basis-32">
                    <Link :href="route('cart')" class="text-gray-500 hover:font-semibold uppercase ml-5">Корзина (0)</Link>
                </div>
                
            </div>
        </nav>
        <nav ref="el" v-on:click="toggleModal()" class="flex py-3 lg:hidden justify-end">
            <button id="menu-switch"  class="hamburger px-4 hamburger--collapse" type="button">
                <span class="hamburger-box">
                    <span class="hamburger-inner"></span>
                </span>
            </button>         
        </nav>
        <!-- <div v-if="showModal" class="overflow-x-hidden overflow-y-auto fixed inset-0 z-50 outline-none focus:outline-none justify-center items-center flex"></div> -->
        <div class="mb-auto">
            <transition name="fade">
            <div v-if="showModal">
                    <div class="relative">
                        <div class="border-0 relative flex flex-col bg-white outline-none focus:outline-none">
                            <div class="relative pl-0 lg:pl-6 pt-4 flex-auto">
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    О нас
                                </a>
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    Магазин
                                </a>
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    Lookbook
                                </a>
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    блог
                                </a>
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    Контакты
                                </a>                            
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    поиск
                                </a>                            
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    войти
                                </a>                            
                                <a href="#" class="block text-gray-600 text-center mb-3 transition duration-300 uppercase">
                                    корзина (0)
                                </a>                            
                            </div>
                        </div>
                    </div> 
                </div>
            </transition>
            <!-- <div v-if="showModal" class="opacity-25 fixed inset-0 z-40 bg-black"></div> -->
        </div>
        <!-- Page Content -->
        <main>
            <slot />
        </main>
        <div class="flex justify-center">
            <footer class="flex flex-wrap justify-center">
                <a href="#" class="group text-gray-500 hover:text-gray-800 text-center mb-3 transition duration-300 uppercase mx-3 my-1 w-full sm:w-auto">
                    связаться с нами
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400 hidden lg:flex"></span>
                </a> 
                <a href="#" class="group text-gray-500 hover:text-gray-800 text-center mb-3 transition duration-300 uppercase mx-3 my-1 w-full sm:w-auto">
                    доставка и оплата
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400 hidden lg:flex"></span>
                </a> 
                <a href="#" class="group text-gray-500 hover:text-gray-800 text-center mb-3 transition duration-300 uppercase mx-3 my-1 w-full sm:w-auto">
                    Возврат и обмен
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400 hidden lg:flex"></span>
                </a> 
                <a href="#" class="group text-gray-500 hover:text-gray-800 text-center mb-3 transition duration-300 uppercase mx-3 my-1 w-full sm:w-auto">
                    Пресса
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400 hidden lg:flex"></span>
                </a> 
                <a href="#" class="group text-gray-500 hover:text-gray-800 text-center mb-3 transition duration-300 uppercase mx-3 my-1 w-full sm:w-auto">
                    отзывы
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400 hidden lg:flex"></span>
                </a> 
                <a href="#" class="group text-gray-500 hover:text-gray-800 text-center mb-3 transition duration-300 uppercase mx-3 my-1 w-full sm:w-auto">
                    Политика конфиденциальности
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400 hidden lg:flex"></span>
                </a> 
                <a href="#" class="group text-gray-500 hover:text-gray-800 text-center mb-3 transition duration-300 uppercase mx-3 my-1 w-full sm:w-auto">
                    ПРАВИЛА И УСЛОВИЯ
                    <span class="block max-w-0 group-hover:max-w-full transition-all duration-500 h-0.5 bg-gray-400 hidden lg:flex"></span>
                </a> 
            </footer>
        </div>
    </div>
    </div>
</template>
