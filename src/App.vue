<template>
  <BaseNavbar />
  <BaseForm :addMessage="addMessage" />

  <Messages :messages="messages" />
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
