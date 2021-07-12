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
                <form>
                  <label class="block text-sm font-medium text-gray-700">Message</label>
                  <div class="mt-1">
                    <input v-model="message" type="text" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md" placeholder="Message" />
                  </div>
                  <label class="mt-2 block text-sm font-medium text-gray-700">Donation</label>
                  <div class="mt-1">
                    <input v-model="donation" type="number" class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 block w-full sm:text-sm border-gray-300 rounded-md" placeholder="0" />
                  </div>
                  <button @click="onSubmit" type="button" class="mt-4 inline-flex items-center px-3 py-2 border border-transparent shadow-sm text-sm leading-4 font-medium rounded-md text-white near-orange focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                    Send message
                    <MailIcon class="ml-2 -mr-0.5 h-4 w-4" aria-hidden="true" />
                  </button>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";

import { MailIcon } from "@heroicons/vue/solid";

import { wallet } from "@/services/near";

export default {
  props: {
    addMessage: {
      type: Function,
      required: true
    }
  },
  components: {
    MailIcon
  },
  setup(props) {
    const message = ref("");
    const donation = ref("0");
    const onSubmit = () => {
      props.addMessage({ text: message.value, donation: donation.value });
    };
    return {
      message,
      donation,
      onSubmit,
      accountId: wallet.getAccountId()
    };
  }
};
</script>
<style scoped>
.near-orange {
  background-color: #ff585d;
}
.near-orange:hover {
  font-weight: 700;
}
</style>
