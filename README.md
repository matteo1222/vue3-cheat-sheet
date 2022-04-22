# Vue3 Cheat Sheet
## Composition API
### ref (The Vue2 data property)
```Vue
<script setup>
    import { ref } from 'vue'
    const title = ref('')       // Declare a reactive state 
    title.value = 'Hello World' // Update the state
</script>
<template>
    <!-- Accessing the state, no need for the '.value' -->
    <h1>{{ title }}</h1>
</template>
```

### computed
### watch
### component
### props
### emit

## \<script setup\>
## Teleport
## Fragments
## Suspense (Experimental)