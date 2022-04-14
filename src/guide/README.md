# Getting Started

## Introduction

BootstrapVue Editable Table component adds new features to [BootstrapVue Table](https://bootstrap-vue.org/docs/components/table) to easily enable cell/row editing, input validation and other features!

> :warning: This library does not work on Vue 3 and Bootstrap 5 becuase [BootstrapVue](https://bootstrap-vue.org) still does not support them.

## Prerequisite

A basic understanding of [BootstrapVue Table](https://bootstrap-vue.org/docs/components/table).

You're required to install Bootstrap and Bootstrap Vue in your project:

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