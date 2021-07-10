<template>
  <BaseNavbar />
  <BaseForm :addMessage="addMessage" />
  <div class="w-full grid justify-center mt-8">
    <Messages :messages="messages" />
  </div>
</template>

<script>
import BaseNavbar from "@/components/BaseNavbar";
import BaseForm from "@/components/BaseForm";
import Messages from "@/components/Messages";

import { useMessages } from "@/composables/near.js";

export default {
  setup() {
    const { messages, addMessage } = useMessages();
    return { messages, addMessage };
  },
  components: {
    BaseNavbar,
    Messages,
    BaseForm
  }
};
</script>

<style></style>
