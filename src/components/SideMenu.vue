<template>
    <div class="menu-wrapper">
      <div v-for="(item, index) in menuConfig" :key="index" :data-testid="'first-level-' + item.title.toLowerCase()">
        <div>{{ item.title }}</div>
        <button v-if="hasSubItems(item)" :data-testid="'button-' + item.title.toLowerCase()" @click="toggleSubmenu(item.title)">
          {{ isExpanded(item.title) ? 'Collapse' : 'Hide' }}
        </button>
        <ul v-if="isExpanded(item.title)" :data-testid="'ul-' + item.title.toLowerCase()">
          <li v-for="(subItem, subIndex) in item.subItems" :key="subIndex" :data-testid="'li-' + item.title.toLowerCase() + '-' + subItem.toLowerCase()">{{ subItem }}</li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "sidemenu",
    props: ["menuConfig"],
    data() {
      return {
        expandedMenus: []
      };
    },
    methods: {
      hasSubItems(item) {
        return item.subItems && item.subItems.length > 0;
      },
      toggleSubmenu(title) {
        const index = this.expandedMenus.indexOf(title);
        if (index === -1) {
          this.expandedMenus.push(title);
        } else {
          this.expandedMenus.splice(index, 1);
        }
      },
      isExpanded(title) {
        return this.expandedMenus.includes(title);
      },
      buttonText(item) {
        return this.isExpanded(item.title) ? 'Collapse' : 'Expand';
      }
    }
  };
  </script>
  
  <style scoped>
  /* Add your CSS styles here */
  </style>