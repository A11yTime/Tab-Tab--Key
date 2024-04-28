<template>
<div>
  <ul role="tablist" class="tablist">
    <li v-for="(tab, index) in tabs" :key="index">
      <button 
        class="tab"
        role="tab"
        :class="{ 'active': index === activeTab }"
        :aria-selected="index === activeTab ? 'true' : 'false'"
        :aria-controls="'panel' + index"
        @click="activeTab = index"
        tabindex="0"
      >
        {{ tab.name }}
      </button>
    </li>
  </ul>

  <div v-for="(tab, index) in tabs" 
  :key="index" :id="'panel'+index" 
  class="tabpanel" role="tabpanel" 
  :aria-labelledby="'tab'+index" 
  :aria-hidden="index !== activeTab"
  :class="{ 'active': index === activeTab }"
  >
  <a href="https://www.williams-sonoma.com/">
    <img :src="tab.image" :alt="tab.alt" />
  </a>
    
  </div>
</div>
</template>

<script>
export default {
  name: 'ManualTab',
  data() {
    return {
      activeTab: 0,
      tabs: [
        { image: '/Images/image1.jpg', name: 'Tab 1', alt: 'Images description goes here' },
        { image: '/Images/image2.jpg', name: 'Tab 2', alt: 'Imgage description goes here' },
        { image: '/Images/image3.jpg', name: 'Tab 3', alt: 'Images description goes here' }
      ]
    }
  },
}
</script>

<style scoped>
  .tablist {
    display: flex;
    list-style-type: none;
    padding: 0;
    margin: 0;
  }
  .tab {
    padding: 10px;
    cursor: pointer;
    border: 1px solid #ccc;
    border-bottom: none;
    background-color: #f1f1f1;
    margin-right: 5px;
  }
  .tab.active {
    background-color: #fff;
    border-bottom: 3px solid #0e0c0c;
  }
  .tabpanel {
    margin-top: 5px;
    display: none;
    padding: 10px;
    border: 1px solid #cccccc;
    outline-offset: 1px;
  }
  .tabpanel.active {
    display: block;
  }
  img {
    height: 100%;
    width: 100%;
  }
 
</style>
