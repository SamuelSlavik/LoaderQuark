# Loader Quark

This quark is a simple vue plugin with a loader component.

## Installation

```sh
npm install loader-quark --save
```

## Setup

main.js
```js
//...
import {Loader} from "loader-quark"
import "loader-quark/dist/style.css"

//...
const app = createApp(App)
//...

app.use(Loader)
```
Import the quark and its styles in the main javascript file and use it as a plugin in your app.

## Basic Usage

AnyComponent.js
```vue
<script setup>
   //...
   const loading = ref(false)
   
   // Perform some data loading, for example some api call
   try {
       loading.value = true // Set loading to true in the beginning
       const response = await fetch('https://api.example.com/data')
       const data = await response.json()
   } catch (error) {
       console.error(error)
   } finally {
       loading.value = false // After the data is loaded, set loading to false
   }
</script>

<template>
   <Loader v-if="loading" type="spinner" primary-color="#7842f5"/>
   <div v-else>
      <!-- ... -->
   </div>
</template>
```
You can use easy conditional rendering to display the loader component for example when waiting for your data to load from backend.
