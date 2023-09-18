<template>
  <!-- 1. Template Syntax -->
  <div>
    <p>{{ message }}</p> <!-- a. Text Interpolation -->
    <p v-html="rawHTML"></p> <!-- b. Raw HTML -->
    <div :id="elementId"></div> <!-- c. Attribute Bindings -->
    <p>{{ 2 + 2 }}</p> <!-- d. JavaScript expressions inside syntax -->
  </div>

  <!-- 2. Methods -->
  <button @click="sayHello">Say Hello</button>

  <!-- 3. Reactivity Fundamentals -->
  <p>{{ reactiveValue }}</p>

  <!-- 4. Computed Properties -->
  <p>Computed Property: {{ computedValue }}</p>

  <!-- 5. Class and Style Bindings -->
  <div :class="{'active': isActive, 'error': hasError}" :style="{'color': textColor}">Styled Div</div>

  <!-- 6. List Rendering -->
  <ul>
    <li v-for="(item, index) in objectList" :key="index">{{ item }}</li> <!-- a. v-for with an Object -->
    <li v-for="n in 5" :key="n">{{ n }}</li> <!-- b. v-for with a Range -->
    <template v-for="item in items">
      <li>{{ item }}</li> <!-- c. v-for on <template> -->
      <li v-if="shouldShow(item)">Conditional Item</li> <!-- d. v-for with v-if -->
    </template>
    <my-component v-for="compItem in components" :key="compItem.id" :item="compItem"></my-component> <!-- e. v-for with a Component -->
  </ul>

  <!-- 7. Event Handling -->
  <button @click="inlineHandler">Inline Handler</button> <!-- a. Inline Handlers -->
  <button @click="methodHandler">Method Handler</button> <!-- b. Method Handlers -->

  <!-- 8. Form Input Bindings -->
  <input type="text" v-model="textModel"> <!-- a. v-model with <input type="text"> -->
  <input type="checkbox" v-model="checkboxModel"> <!-- a. v-model with <input type="checkbox"> -->
  <input type="radio" v-model="radioModel" value="option1"> <!-- a. v-model with <input type="radio"> -->
  <select v-model="selectedOption"> <!-- a. v-model with <select> -->
    <option value="option1">Option 1</option>
    <option value="option2">Option 2</option>
  </select>
  <textarea v-model="textareaModel"></textarea> <!-- a. v-model with <textarea> -->

  <!-- 9. Watchers -->
  <input type="text" v-model="watcherModel"> <!-- This will trigger a watcher -->

  <!-- 10. Components -->
  <child-component :prop1="parentProp" @custom-event="handleCustomEvent">
    <template v-slot:default>
      <!-- Slot Content -->
    </template>
  </child-component>

  <!-- 11. Router -->
  <router-link to="/page">Go to Page</router-link>
  <router-view></router-view>
</template>

<script>
import { ref, computed, watch } from 'vue';

export default {
  data() {
    return {
      // 1. Template Syntax
      message: 'Hello, Vue!',
      rawHTML: '<span style="color: red;">Red Text</span>',
      elementId: 'unique-id',

      // 3. Reactivity Fundamentals
      reactiveValue: ref(0),

      // 4. Computed Properties
      a: 2,
      b: 3,
    };
  },
  computed: {
    computedValue() {
      return this.a + this.b;
    },
  },
  methods: {
    sayHello() {
      alert('Hello!');
    },
    // 7. Event Handling
    inlineHandler() {
      alert('Inline Handler');
    },
    methodHandler() {
      alert('Method Handler');
    },
    // 9. Watchers
    watcherModel(newValue, oldValue) {
      console.log('Watcher triggered:', newValue, oldValue);
    },
    // 10. Components
    handleCustomEvent(data) {
      console.log('Custom event received:', data);
    },
  },
  // 5. Class and Style Bindings
  data() {
    return {
      isActive: true,
      hasError: false,
      textColor: 'blue',
    };
  },
  // 6. List Rendering
  data() {
    return {
      objectList: { a: 'Apple', b: 'Banana', c: 'Cherry' },
      items: [1, 2, 3, 4, 5],
      components: [{ id: 1, name: 'Component A' }, { id: 2, name: 'Component B' }],
    };
  },
  methods: {
    shouldShow(item) {
      return item > 2;
    },
  },
  // 8. Form Input Bindings
  data() {
    return {
      textModel: '',
      checkboxModel: false,
      radioModel: 'option1',
      selectedOption: 'option1',
      textareaModel: '',
    };
  },
  // 9. Watchers
  watch: {
    textModel(newValue, oldValue) {
      console.log('Text Model Watcher:', newValue, oldValue);
    },
  },
  // 10. Components
  components: {
    ChildComponent: {
      props: ['prop1'],
      template: `
        <div>
          <slot></slot>
          <button @click="emitCustomEvent">Trigger Event</button>
        </div>
      `,
      methods: {
        emitCustomEvent() {
          this.$emit('custom-event', { message: 'Custom event data' });
        },
      },
    },
  },
};
</script>
