<template>
  <!-- Header -->
  <div
    class="fixed w-full flex items-center justify-between h-14 text-white z-10"
  >
    <div
      class="
        flex
        items-center
        justify-start
        md:justify-center
        pl-3
        w-14
        md:w-64
        h-14
        bg-blue-800
        dark:bg-gray-800
        border-none
      "
    >
      <div
        v-if="user != null"
        class="relative"
        v-click-outside="
          () => {
            isOpen = false;
          }
        "
      >
        <button
          @click="isOpen = !isOpen"
          class="
            flex flex-row
            items-center
            w-full
            px-1
            py-1
            mt-2
            text-sm
            font-semibold
            text-left
            bg-transparent
            rounded-full
            md:w-auto md:mt-0 md:ml-2
            hover:text-gray-900
            focus:text-gray-900
            hover:bg-gray-200
            focus:bg-gray-200 focus:outline-none focus:shadow-outline
          "
        >
          <img
            :src="APP_URL + 'images/users_images/' + user.user_image"
            class="w-auto h-6 rounded-full"
            alt=""
          />
        </button>
        <div
          v-show="isOpen"
          class="
            z-10
            absolute
            right-0
            w-full
            mt-2
            origin-top-right
            rounded-md
            shadow-lg
            md:w-48
          "
        >
          <ul
            class="
              px-2
              py-2
              bg-white
              dark:bg-gray-700
              text-black
              dark:text-white
              rounded-md
              shadow
            "
          >
            <li
              class="
                cursor-pointer
                block
                px-4
                py-2
                mt-2
                bg-transparent
                rounded-lg
                text-sm
                font-semibold
                md:mt-0
                hover:bg-blue-500 hover:text-white
                dark:hover:bg-gray-600
                text-white-600
                hover:text-white-800 hover:border-blue-500
                dark:hover:border-gray-800
              "
              @click="logoutUser"
            >
              تسجيل الخروج
            </li>
          </ul>
        </div>
      </div>
      <span v-if="user != null" class="hidden md:block">{{ user.name }}</span>
    </div>
    <div
      class="
        flex
        justify-between
        items-center
        h-14
        bg-blue-800
        dark:bg-gray-800
        header-right
      "
    >
      <div
        class="
          bg-white
          rounded
          flex
          items-center
          w-full
          max-w-xl
          mr-4
          p-2
          shadow-sm
          border border-gray-200
        "
      >
        <button class="outline-none focus:outline-none">
          <svg
            class="w-5 text-gray-600 h-5 cursor-pointer"
            fill="none"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
          </svg>
        </button>
        <input
          type="search"
          name=""
          id=""
          placeholder="Search"
          class="
            w-full
            pl-3
            text-sm text-black
            outline-none
            focus:outline-none
            bg-transparent
          "
        />
      </div>
      <ul class="flex items-center">
        <li>
          <button
            aria-hidden="true"
            @click="$emit('change_theme')"
            class="
              group
              p-2
              transition-colors
              duration-200
              rounded-full
              shadow-md
              bg-blue-200
              hover:bg-blue-200
              dark:bg-gray-50 dark:hover:bg-gray-200
              text-gray-900
              focus:outline-none
            "
          >
            <svg
              v-show="isDark"
              width="24"
              height="24"
              class="
                fill-current
                text-gray-700
                group-hover:text-gray-500
                group-focus:text-gray-700
                dark:text-gray-700
                dark:group-hover:text-gray-500
                dark:group-focus:text-gray-700
              "
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke=""
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"
              />
            </svg>
            <svg
              v-show="!isDark"
              width="24"
              height="24"
              class="
                fill-current
                text-gray-700
                group-hover:text-gray-500
                group-focus:text-gray-700
                dark:text-gray-700
                dark:group-hover:text-gray-500
                dark:group-focus:text-gray-700
              "
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke=""
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"
              />
            </svg>
          </button>
        </li>
        <li>
          <div class="block w-px h-6 mx-3 bg-gray-400 dark:bg-gray-700"></div>
        </li>
        <li>
          <a href="#" class="flex items-center mr-4 hover:text-blue-100">
            <span class="inline-flex mr-1">
              <svg
                class="w-5 h-5"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1"
                ></path>
              </svg>
            </span>
            خروج
          </a>
        </li>
      </ul>
    </div>
  </div>
  <!-- ./Header -->
</template>

<script>
import { ref } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";
import useConfig from "../../config";
import axios from "axios";
import { useRouter } from "vue-router";
export default {
  emits: ["change_theme"],
  props: {
    isDark: {
      type: Boolean,
      default: true,
    },
  },
  setup() {
    const { APP_URL, getHeader } = useConfig();
    const router = useRouter();
    let isOpen = ref(false);
    let user = ref({});
    onMounted(() => {
      user.value = JSON.parse(window.localStorage.getItem("logged_in_user"));
      console.log(user.value);
    });

    async function logoutUser() {
      await axios
        .get("api/logout", { headers: getHeader() })
        .then(async () => {
          await localStorage.removeItem("token");
          await localStorage.removeItem("logged_in_user");
          await location.reload();
          router.push({ name: "login" });
        })
        .catch((error) => {
          console.log(error);
        });
    }
    return { isOpen, user, APP_URL, logoutUser };
  },
};
</script>
