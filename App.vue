<template>
  <div class="container">
    <div class="color-select" @click="toggleDropdown" :style="{backgroundColor:selectedColor}">
      <span>
        {{ selectedText }}
        <span :style="{ backgroundColor: selectedColor }"></span>
      </span>
      <ul v-if="showDropdown">
        <li 
          v-for="color in colors"
          :key="color.value"
          :style="{ backgroundColor: color.value }"
          @click="selectColor(color)"
        >
          <!-- <span>{{ color.text }}</span> -->
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showDropdown: false,
      selectedColor: '#ffffff',
      colors: [
        { value: '#ffffff', text: 'White' },
        { value: '#2ecc71', text: 'Green' },
        { value: '#3498db', text: 'Blue' },
        { value: '#9b59b6', text: 'Purple' },
        { value: '#34495e', text: 'Dark Blue' },
        { value: '#1abc9c', text: 'Turquoise' },
        { value: '#e74c3c', text: 'Red' },
        { value: '#7f8c8d', text: 'Grey' },
        { value: '#f1c40f', text: 'Yellow' },
        { value: '#e67e22', text: 'Orange' },
        { value: '#000000', text: 'Black' }
      ]
    };
  },
  methods: {
    toggleDropdown() {
      this.showDropdown = !this.showDropdown;
    },
    selectColor(color) {
      this.selectedColor = color.value;
      this.selectedText = color.text;
      this.showDropdown = false;
    }
  }
};
</script>

<style scoped>
body {
  background: #222;
  color: #fff;
  font-family: helvetica;
  font-size: 13px;
}

.container {
  margin: 0px auto;
  width: 30px;
  height: 30px;
  border-radius: 50%;
}

.color-select {
  border: 1px solid #3E3E3E;
  padding: 10px;
  cursor: pointer;
  position: relative;
  width: 30px;
  height: 30px;
  border-radius: 50%;
}

/* .color-select > span {
  text-transform: uppercase;
  padding: 8px 0;
  display: block;
  content: icon;
} */

/* .color-select > span span {
  margin-top: -8px;
  display: inline-block;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  vertical-align: middle;
} */

.color-select ul {
  width: 100%;
  overflow: visible;
  padding: 0;
  border-top: 1px solid #3E3E3E;
  position: absolute;
  top: 100%;
  left: 0;
  background: #222;
  z-index: 1000;
}

.color-select ul:after {
  display: table;
  clear: both;
}

.color-select ul li,
/* .color-select > span span {
  list-style: none;
  width: 30px;
  height: 30px;
  display: block;
  border-radius: 50%;
  background: #fff;
  float: left;
  margin: 0 12px;
  cursor: pointer;
  position: relative;
  top: -7px;
} */

.color-select ul li {
  transition: all 0.3s ease-in-out;
}

.color-select ul li span {
  display:none;
}

.color-select ul li:hover {
  transform: scale(1.15);
}
</style>
