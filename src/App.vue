<template>
  <div id="app"></div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { Node } from "@/types/node";

@Component
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

