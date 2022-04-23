# Vue3 Cheat Sheet
## Composition API
### ref (equivalent to the Vue2 data property)
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
```Vue
<script setup>
    import { ref, computed } from 'vue'
    const firstName = ref('John')
    const lastName = ref('Doe')
    // a read-only computed
    const fullName = computed(() => {
        return `${firstName.value} ${lastName.value}`
    })
    // a writable computed
    const fullNameWritable = computed({
        get: () => `${firstName.value} ${lastName.value}`,
        set: (newName) => {
            firstName.value = newName.split(' ')[0]
            lastName.value = newName.split(' ')[0]
        }
    })
</script>
<template>
    <!-- Accessing the state, no need for the '.value' -->
    <h1>{{ fullName }}</h1>
</template>
```
### watch
```Vue
<script setup>
    import { ref, watch } from 'vue'
    const count = ref(0)
    const firstRef = ref('')
    const secondRef = ref('')
    watch(count, (count, prevCount) => {
        console.log(count, prevCount)
    })
    // watching multiple ref
    watch([firstRef, secondRef], ([firstVal, secondVal], [prevFirstVal, prevSecondVal]) => {
        console.log(firstVal, secondVal)
    })
</script>
<template>
    <!-- Accessing the state, no need for the '.value' -->
    <h1>{{ count }}</h1>
</template>
```
### components
```Vue
<script setup>
    import NavBar from './NavBar.vue'
</script>
<template>
    <NavBar />
</template>
```
### props
```Vue
<!-- In a child component -->
<script setup>
    const props = defineProps({
        isLoggedIn: Boolean
    })
</script>
<template>
    <h1>{{ isLoggedIn ? 'Logged In' : 'Not Logged In Yet' }}</h1>
</template>
```
```Vue
<!-- In a parent component -->
<script setup>
    import ChildComp from './ChildComp.vue'
</script>
<template>
    <!-- Use kebab-case for passing the props -->
    <ChildComp :is-logged-in="true" />
</template>
```
### emit
```Vue
<!-- In a child component -->
<script setup>
    const emit = defineEmits('mouseMove', 'formSubmit')
    emit('mouseMove')
</script>
<template>
    <h1>Child</h1>
</template>
```

## Teleport
## Fragments
## Suspense (Experimental)