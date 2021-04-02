<template>
  <v-container fluid>
    <div class="pills">
      <Pill
        v-for="word in groupedWords"
        :key="word.name"
        :name="word.name"
        :amount="word.amount"
      />
    </div>
    <Chat />
  </v-container>
</template>

<script>
import Pill from "./Pill";
import Chat from "./Chat";

export default {
  components: { Pill, Chat },
  data: function() {
    return {
      groupedWords: [
        { name: "i", amount: 1234 },
        { name: "you", amount: 900 },
        { name: "he", amount: 853 },
      ],
    };
  },
};
</script>

<style>
.pills {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
