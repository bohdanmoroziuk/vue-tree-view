<template>
  <div class="TreeView">
    <div class="TreeView-node" @click="toggle">
      <span class="TreeView-nodeIcon" v-html="nodeIcon" v-if="hasChildren"></span>
      <span class="TreeView-nodeIcon" v-else>&#9671;</span>
      <p class="TreeView-nodeName">{{node.name}}</p>
    </div>
    <div class="TreeView-children" v-if="expended" :style="childrenStyle">
      <TreeView
        v-for="child of node.children"
        :key="child.name"
        :node="child"
        :depth="childrenDepth"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Prop, Component } from 'vue-property-decorator';
import { Node } from '@/types/node';

@Component
export default class TreeView extends Vue {
  // Props

  @Prop()
  public readonly node!: Node;

  @Prop({
    default: 1,
    validator: (value: number): boolean => value >= 0,
  })
  public readonly depth!: number;

  // Data

  public expended: boolean = false;

  public offsetStep: number = 12;

  // Computed

  get childrenDepth(): number {
    return this.depth + 1;
  }

  get childrenStyle() {
    return { 'margin-left': `${this.offsetStep * this.depth}px` };
  }

  get hasChildren(): boolean {
    return !!this.node.children && !!this.node.children.length;
  }

  get nodeIcon(): string {
    return this.expended ? '&#9660;' : '&#9658;';
  }

  // Methods
  public toggle() {
    this.expended = !this.expended;
  }
}
</script>

<style scoped>
.TreeView-node {
  display: flex;
  align-items: center;
  cursor: pointer;
  padding-right: 0.25rem;
  padding-left: 0.25rem;
  transition: background-color 0.25s ease-in-out;
}

.TreeView-node:hover {
  background-color: #555;
}

.TreeView-nodeIcon {
  margin-right: 0.5rem;
}
</style>