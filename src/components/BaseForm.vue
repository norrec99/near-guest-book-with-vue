<template>
  <div class="bg-red relative pt-16 pb-32 overflow-hidden">
    <div aria-hidden="true" class="absolute inset-x-0 top-0 h-48 bg-gradient-to-b from-gray-100" />
    <div class="relative">
      <div class="lg:mx-auto lg:max-w-7xl lg:px-8 lg:grid lg:grid-cols-2 lg:grid-flow-col-dense lg:gap-24">
        <div class="px-4 max-w-xl mx-auto sm:px-6 lg:py-16 lg:max-w-none lg:mx-0 lg:px-0">
          <div>
            <div class="mt-6">
              <h2 class="text-3xl font-extrabold tracking-tight text-gray-900">Welcome {{ accountId }}</h2>
              <p class="mt-4 text-lg text-gray-500">Sign in with NEAR and add a message to the guest book!</p>
              <div class="mt-6">
                <label class="block text-sm font-medium text-gray-700">Message</label>
                <div class="mt-1">
                  <input type="text" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md" placeholder="Message" />
                </div>
                <label class="block text-sm font-medium text-gray-700">Message</label>
                <div class="mt-1">
                  <input type="text" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md" placeholder="Message" />
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-12 sm:mt-16 lg:mt-0">
          <div class="pl-4 -mr-48 sm:pl-6 md:-mr-16 lg:px-0 lg:m-0 lg:relative lg:h-full">
            <img class="w-full rounded-xl shadow-xl ring-1 ring-black ring-opacity-5 lg:absolute lg:left-0 lg:h-full lg:w-auto lg:max-w-none" src="https://near-guestbook.onrender.com/img/hero.57ea1a39.png" alt="Inbox user interface" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";

import { wallet } from "@/services/near";

export default {
  setup(props) {
    const message = ref("");
    const donation = ref(null);
    const onSubmit = () => {
      props.addMessages({ text: message.value, donation: donation.value });
    };
    return {
      message,
      donation,
      onSubmit,
      accountId: wallet.getAccountId()
    };
  },
  props: {
    addMessages: {
      type: Function,
      required: true
    }
  }
};
</script>
