<template>
  <q-page class="flex column">
    <div class="q-pa-md column col justify-end">
      <q-chat-message
        v-for="message in messages"
        :key="message.text"
        :name="message.from"
        :text="[message.text]"
        :sent="message.from === 'me'"
      />
    </div>
    <q-footer elevated>
      <q-toolbar>
        <q-form @submit="sendMessage" class="full-width">
          <div class="row justify-between">
            <q-input
              class="col-11"
              v-model="newMessage"
              label="Message"
              bg-color="white"
              rounded
              outlined
              dense
            >
            </q-input>
            <q-btn
              class="col-1"
              round
              dense
              flat
              color="white"
              icon="send"
              type="submit"
            />
          </div>
        </q-form>
      </q-toolbar>
    </q-footer>
  </q-page>
</template>

<script>
import { defineComponent, ref, reactive } from "vue";

export default defineComponent({
  setup() {
    // This variable will store a new message
    const newMessage = ref("");

    // This variable contains a list of all messages

    const messages = reactive([
      {
        text: "Ola",
        from: "me",
      },
      {
        text: "Beleza?",
        from: "Rafael",
      },
      {
        text: "Tudo joia...",
        from: "me",
      },
    ]);

    // This method will send a new message to the recipient
    const sendMessage = () => {
      if (newMessage.value.trim().length) {
        messages.push({
          text: newMessage.value,
          from: "me",
        });
        newMessage.value = "";
      }
    };

    return {
      newMessage,
      messages,
      sendMessage,
    };
  },
});
</script>
