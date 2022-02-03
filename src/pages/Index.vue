<template>
  <q-page class="flex flex-center">
    <q-input dense flat autofocus v-model="text"> </q-input>
    <q-btn color="primary" @click="onSendClick"> Получить смысл </q-btn>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import API from "../api/api";

export default defineComponent({
  name: "PageIndex",

  setup() {
    let text =
      "Главный герой всю жизнь занимается финансовыми махинациями. Это не только приносит ему солидные деньги, но и удовольствие от столь рискованных предприятий. На этот раз он решает взломать компьютерную систему государственного банка и завладеть суммой денег, которой ему хватит до конца жизни. Но нужен напарник, хорошо разбирающийся в компьютерах. Он находит одного парня, отбывшего срок за финансовое преступление. Тот не хочет возвращаться в тюрьму и отказывает мошеннику, но вскоре соглашается. А немногим позже компьютерщик понимает, что на свою долю он может не рассчитывать: его попросту используют. Между напарниками начинается настоящая война за ещё не добытые деньги.";
    return {
      text,
    };
  },
  // // Хук который сработает когда страница создасться
  // mounted() {
  //   this.userName = "Login";
  //   this.intervalCtx = setInterval(async () => {
  //     try {
  //       const msg = await API.getMessage(this.lastMsgID);
  //       if (typeof msg === typeof {}) {
  //         this.messages.push(msg);
  //         this.lastMsgID++;
  //       }
  //     } catch (e) {}
  //   }, 1000);
  // },
  // unmounted() {
  //   clearInterval(this.intervalCtx);
  // },
  methods: {
    // Реакция на кнопку отправки
    async onSendClick() {
      try {
        this.mas = await API.sendMessage(this.text);
        console.log(this.mas);
      } catch (e) {
        console.error(e);
      }
    },
    fontSizeMapper: (word) => Math.log2(word.value) * 5,
  },
});
</script>
