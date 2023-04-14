<template>
  <v-app>
    <template>
      <div>
        <articleComponent :jsondata="testData"></articleComponent>
      </div>
    </template>
  </v-app>
</template>
<script>
// @ is an alias to /src
import articleComponent from "@/components/article";
import testData from "@/assets/json/test.json";
export default {
  name: "App",
  components: { articleComponent },
  data() {
    return {
      testData: "",
    };
  },
  methods: {},
  mounted() {
    var self = this;
    self.testData = testData;
  },
};
</script>

<style lang="scss">

</style>
