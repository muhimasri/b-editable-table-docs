# Getting Started

## Introduction

BootstrapVue Editable Table provides new features to [BootstrapVue Table](https://bootstrap-vue.org/docs/components/table) that easily enable cell/row editing, input validation, and other gems while keeping all existing functionalities of the original table intact!

> :warning: This library does not work with Vue 3 and Bootstrap 5 because [BootstrapVue](https://bootstrap-vue.org) still does not support it.

## Prerequisite

A basic understanding of [BootstrapVue Table](https://bootstrap-vue.org/docs/components/table).

You're required to install Bootstrap and Bootstrap Vue in your project (any version earlier than Bootstrap 5):

```bash
npm install bootstrap bootstrap-vue
```

## Setup
```bash
npm i bootstrap-vue-editable-table
```
Since this is a BootstrapVue component, you need to set it up the same way. The easiest approach is to register BootstrapVue in your app entry point (typically app.js or main.js):

```javascript
import Vue from 'vue'
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'

// Import Bootstrap and BootstrapVue CSS files (order is important)
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue)
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin)
```
Please refer to [BoostrapVue Docs](https://bootstrap-vue.org/docs) for more details.