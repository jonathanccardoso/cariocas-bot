<template>
  <v-container fluid>
    <h2>Pedidos</h2>

    <div class="pills">
      <Pill
        v-for="word in groupedWords"
        :key="word.name"
        :name="word.name"
        :amount="word.amount"
      />
    </div>

    <h2>Gráficos Covid Brasil</h2>
    <span>Como estamos meio a pandêmia, veja como está situação!</span> <br />
    <span>*Utilizando a api <b>https://covid19.mathdro.id/api</b> </span>
    <div class="wrapper">
      <BarChart />
    </div>

    <!-- <script
      defer
      src="https://www.gstatic.com/dialogflow-console/fast/messenger/bootstrap.js?v=1"
    ></script> -->
    <df-messenger
      intent="WELCOME"
      chat-title="Pizzaria"
      agent-id="5009165b-2ecc-4d5f-a3d7-c80692e177ec"
      language-code="pt-br"
    ></df-messenger>
  </v-container>
</template>

<script>
import Pill from "./Pill";
import BarChart from "./BarChart";

export default {
  components: { Pill, BarChart },
  data: function() {
    return {
      groupedWords: [
        { name: "Pizza Sertaneja", amount: 10 },
        { name: "Pizza Mussarela", amount: 9 },
        { name: "Pizza Calabresa", amount: 20 },
      ],
    };
  },
  mounted() {
    let externalScript = document.createElement("script");
    externalScript.setAttribute(
      "src",
      "https://www.gstatic.com/dialogflow-console/fast/messenger/bootstrap.js?v=1"
    );
    document.head.appendChild(externalScript);
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

<style>
df-messenger {
  --df-messenger-bot-message: #878fac;
  --df-messenger-button-titlebar-color: #df9b56;
  --df-messenger-chat-background-color: #fafafa;
  --df-messenger-font-color: white;
  --df-messenger-send-icon: #878fac;
  --df-messenger-user-message: #479b3d;
}
</style>
