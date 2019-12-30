<template>
  <div class="app" id="app">
    <TreeView :node="node" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Node } from "@/types/node";

import TreeView from "@/components/TreeView.vue";

@Component({
  components: {
    TreeView
  }
})
export default class App extends Vue {
  node: Node = {
    name: "vue-tree-view",
    children: [
      {
        name: "public",
        children: [
          {
            name: "index.html"
          },
          {
            name: "favicon.ico"
          }
        ]
      },
      {
        name: "src",
        children: [
          {
            name: "assets",
            children: [
              {
                name: "logo.png"
              }
            ]
          },
          {
            name: "components",
            children: [
              {
                name: "TreeView.vue"
              }
            ]
          }
        ]
      },
      {
        name: "test",
        children: [
          {
            name: "unit",
            children: [
              {
                name: "example.spec.ts"
              }
            ]
          }
        ]
      }
    ]
  };
}
</script>

