<template>
  <div>
    <div class="text-center bg-green-700 py-2">
      <h1 class="text-white">
        Welcome To Website - <strong class="text-yellow-300">Pokemon GO</strong>
      </h1>
    </div>
    <nav
      class="bg-green-500 border-gray-200 px-2 sm:px-4 py-2.5 rounded dark:bg-gray-900"
    >
      <div
        class="container flex flex-wrap justify-between items-center mx-auto"
      >
        <router-link to="/" class="flex items-center">
          <img
            src="../assets/img/pokemonlogo.png"
            class="mr-3 h-10 sm:h-20"
            alt="Flowbite Logo"
          />
        </router-link>
        <div class="flex items-center md:order-2">
          <!-- Dropdown menu -->
          <div
            class="hidden z-50 my-4 text-base list-none bg-white rounded divide-y divide-gray-100 shadow dark:bg-gray-700 dark:divide-gray-600"
            id="user-dropdown"
            data-popper-reference-hidden=""
            data-popper-escaped=""
            data-popper-placement="bottom"
            style="position: absolute; inset: 0px auto auto 0px; margin: 0px; transform: translate(0px, 14px);"
          >
            <div class="py-3 px-4">
              <span class="block text-sm text-gray-900 dark:text-white"
                >Bonnie Green</span
              >
              <span
                class="block text-sm font-medium text-gray-500 truncate dark:text-gray-400"
                >name@flowbite.com</span
              >
            </div>
            <ul class="py-1" aria-labelledby="user-menu-button">
              <li>
                <a
                  class="block py-2 px-4 text-sm text-gray-700 hover:bg-gray-100 dark:hover:bg-gray-600 dark:text-gray-200 dark:hover:text-white"
                  >Dashboard</a
                >
              </li>
              <li>
                <a
                  class="block py-2 px-4 text-sm text-gray-700 hover:bg-gray-100 dark:hover:bg-gray-600 dark:text-gray-200 dark:hover:text-white"
                  >Settings</a
                >
              </li>
              <li>
                <a
                  class="block py-2 px-4 text-sm text-gray-700 hover:bg-gray-100 dark:hover:bg-gray-600 dark:text-gray-200 dark:hover:text-white"
                  >Earnings</a
                >
              </li>
              <li>
                <a
                  class="block py-2 px-4 text-sm text-gray-700 hover:bg-gray-100 dark:hover:bg-gray-600 dark:text-gray-200 dark:hover:text-white"
                  >Sign out</a
                >
              </li>
            </ul>
          </div>
          <button
            data-collapse-toggle="mobile-menu-2"
            type="button"
            class="inline-flex items-center p-2 ml-1 text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
            aria-controls="mobile-menu-2"
            aria-expanded="false"
          >
            <span class="sr-only">Open main menu</span>
            <svg
              class="w-6 h-6"
              aria-hidden="true"
              fill="currentColor"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
                clip-rule="evenodd"
              ></path>
            </svg>
          </button>
        </div>
        <div
          class="hidden justify-between items-center w-full md:flex md:w-auto md:order-1"
          id="mobile-menu-2"
        >
          <ul
            class="flex flex-col p-4 mt-4 bg-gray-50 rounded-lg border border-gray-100 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700"
          >
            <li>
              <router-link
                class="mr-7 ml-4 block py-2 pr-4 pl-3 text-gray-700 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 dark:text-gray-400 md:dark:hover:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent dark:border-gray-700"
                to="/"
                >Home</router-link
              >
            </li>
            |
            <li>
              <router-link
                class="mr-4 block py-2 pr-4 pl-3 text-gray-700 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 dark:text-gray-400 md:dark:hover:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent dark:border-gray-700"
                to="/About"
                >List Pokemon</router-link
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <br />
  </div>
</template>
