<template>
  <BaseNavbar />
  <Messages :messages="messages" />
</template>

<script>
import BaseNavbar from "@/components/BaseNavbar";
import Messages from "@/components/Messages";

import { useMessages } from "@/composables/near.js";

export default {
  setup() {
    const { messages, addMessage } = useMessages();
    return { messages, addMessage };
  },
  components: {
    BaseNavbar,
    Messages
  }
};
</script>

<style></style>
