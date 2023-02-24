<template>
  <div class="hello">
    <div id="container"></div>
  </div>
</template>

<script>
import { lowerCase } from "lodash";
import * as TVWebSDK from "@tsocial/tvweb-sdk";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data: function () {
    return {
      tv: null,
    };
  },
  mounted() {
    this.tv = new TVWebSDK.SDK({
      container: document.getElementById("container"),
      lang: "vi",
      assetRoot: "https://unpkg.com/@tsocial/tvweb-sdk@4.3.0/assets",
    });
    console.log("cc", this.tv)
    this.tv.readIDCardUIOnly({
      frontCamera: false,
      title: "Mặt trước CMND/CCCD",
      titleIcon: "id_card_front.svg",
      description: "Vui lòng đặt CMND mặt trước vào trong khung",
      onSuccess: (output) => console.log(output),
    });
  },
  methods: {
    lowerCase,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
