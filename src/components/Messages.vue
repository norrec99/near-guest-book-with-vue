<template>
  <div class="rounded-lg bg-gray-200 overflow-hidden shadow divide-y divide-gray-200 sm:divide-y-0 sm:grid sm:grid-cols-2 sm:gap-px md:grid-cols-3">
    <div v-for="(message, index) in messages" :key="index" :class="[index === 0 ? 'rounded-tl-lg rounded-tr-lg sm:rounded-tr-none' : '', index === 1 ? 'sm:rounded-tr-lg' : '', index === messages.length - 2 ? 'sm:rounded-bl-lg' : '', index === messages.length - 1 ? 'rounded-bl-lg rounded-br-lg sm:rounded-bl-none' : '', 'relative group bg-white p-6 focus-within:ring-2 focus-within:ring-inset focus-within:ring-indigo-500']">
      <div>
        <!-- <span class="rounded-lg inline-flex p-3 ring-4 ring-white">
          <BadgeCheckIcon />
        </span> -->
      </div>
      <div class="mt-8">
        <h3 class="text-lg font-medium">
          <a href="#" class="focus:outline-none">
            <!-- Extend touch target to entire panel -->
            <span class="absolute inset-0" aria-hidden="true" />
            {{ message.sender }}
          </a>
        </h3>
        <p class="mt-2 text-sm text-gray-500">{{ message.text }}</p>
      </div>
      <span v-if="message.premium" class="absolute prem-font-conf text-lg top-6 right-6 text-red-400 group-hover:text-red-600" aria-hidden="true"> <BadgeCheckIcon /> Premium </span>
      <span v-else class="absolute heart-font-conf top-6 right-6 text-gray-300 group-hover:text-gray-400" aria-hidden="true"> <HeartIcon /> Love Attached </span>
    </div>
  </div>
</template>

<script>
import { BadgeCheckIcon, HeartIcon } from "@heroicons/vue/outline";
export default {
  setup(props) {
    // eslint-disable-next-line vue/no-setup-props-destructure
    const book = props.messages;
    // console.log(book[0].premium);

    return { book };
  },
  props: {
    messages: {
      type: Object,
      required: true
    }
  },
  components: {
    BadgeCheckIcon,
    HeartIcon
  }
};
</script>

<style scoped>
.heart-font-conf {
  font-size: 7px;
}
.prem-font-conf {
  font-size: 10px;
}
</style>
