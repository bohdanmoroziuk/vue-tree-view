<template>
  <div class="App" id="app">
    <aside class="App-sidebar">
      <TreeView :node="node" />
    </aside>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { Node } from '@/types/node';

import TreeView from '@/components/TreeView.vue';

@Component({
  components: {
    TreeView,
  },
})
export default class App extends Vue {
  public node: Node = {
    name: 'vue-tree-view',
    children: [
      {
        name: 'public',
        children: [
          {
            name: 'index.html',
          },
          {
            name: 'favicon.ico',
          },
        ],
      },
      {
        name: 'src',
        children: [
          {
            name: 'assets',
            children: [
              {
                name: 'logo.png',
              },
            ],
          },
          {
            name: 'components',
            children: [
              {
                name: 'TreeView.vue',
              },
            ],
          },
        ],
      },
      {
        name: 'test',
        children: [
          {
            name: 'unit',
            children: [
              {
                name: 'example.spec.ts',
              },
            ],
          },
        ],
      },
    ],
  };
}
</script>

<style scoped>
.App {
  width: 100%;
  height: 100%;
  background-color: #fff;
  color: #333;
}

.App-sidebar {
  height: 100%;
  max-width: 30%;
  width: 100%;
  overflow: auto;
  padding: 0.25rem 0.5rem;
  background-color: #333;
  color: #fff;
}

@media (min-width: 1370px) {
  .App-sidebar {
    max-width: 20%;
  }
}
</style>