<template>
  <!-- Your template content from the original code -->
</template>

<script setup>
import { ref, computed, watch } from 'vue';

// 1. Template Syntax
const message = ref('Hello, Vue!');
const rawHTML = '<span style="color: red;">Red Text</span>';
const elementId = 'unique-id';

// 3. Reactivity Fundamentals
const reactiveValue = ref(0);

// 4. Computed Properties
const a = 2;
const b = 3;
const computedValue = computed(() => a + b);

// 5. Class and Style Bindings
const isActive = ref(true);
const hasError = ref(false);
const textColor = 'blue';

// 6. List Rendering
const objectList = { a: 'Apple', b: 'Banana', c: 'Cherry' };
const items = [1, 2, 3, 4, 5];
const components = [{ id: 1, name: 'Component A' }, { id: 2, name: 'Component B' }];
const shouldShow = (item) => item > 2;

// 8. Form Input Bindings
const textModel = ref('');
const checkboxModel = ref(false);
const radioModel = ref('option1');
const selectedOption = ref('option1');
const textareaModel = ref('');

// 9. Watchers
watch(textModel, (newValue, oldValue) => {
  console.log('Text Model Watcher:', newValue, oldValue);
});

// 7. Event Handling
const sayHello = () => {
  alert('Hello!');
};
const inlineHandler = () => {
  alert('Inline Handler');
};
const methodHandler = () => {
  alert('Method Handler');
};

// 10. Components
import ChildComponent from '@/components/ChildComponent.vue';

const handleCustomEvent = (data) => {
  console.log('Custom event received:', data);
};
</script>
