# vue3-cron-editor

cron expression editor based on vue3、ts and antd-vue.

English | [简体中文](./README-zh_CN.md)

## Preview

![](public/preview-en.png)

## Supported format

```
*    *    *    *    *    *    *
┬    ┬    ┬    ┬    ┬    ┬    ┬
│    │    │    │    │    |    └ year (currentYear - 2099)
│    │    │    │    │    └───── day of week (0 - 7) (0 or 7 is Sun)
│    │    │    │    └────────── month (1 - 12)
│    │    │    └─────────────── day of month (1 - 31)
│    │    └──────────────────── hour (0 - 23)
│    └───────────────────────── minute (0 - 59)
└────────────────────────────── second (0 - 59)
```

| Field  | Required | Value range      | Allowed wildcard |
| ------ | -------- | ---------------- | ---------------- |
| Second | Yes      | 0-59             | , - \* /         |
| Minute | Yes      | 0-59             | , - \* /         |
| Hour   | Yes      | 0-23             | , - \* /         |
| Date   | Yes      | 1-31             | , - \* / L W     |
| Month  | Yes      | 1-12             | , - \* /         |
| Week   | Yes      | 0-7 or SUN-SAT   | , - \* / L #     |
| Year   | No       | currentYear-2099 | , - \* /         |

## Installation

```
npm install vue3-cron-editor --save
```

## Usage

### Import

```typescript
// Global import.
import { createApp } from 'vue'
import AntDesignVue from 'ant-design-vue'
import 'ant-design-vue/dist/antd.css'
import Vue3Cron from 'vue3-cron-editor'

import App from './App.vue'

const app = createApp(App)

app.use(AntDesignVue)
app.use(Vue3Cron)

app.mount('#app')
```

or

```vue
<script>
import Vue3Cron from 'vue3-cron-editor'
// Single import.
export default {
  components: {
    Vue3Cron,
  },
}
</script>
```

### Use

```vue
<template>
  <vue3-cron v-model="expression" :locale="locale" />
</template>

<script>
export default {
  data() {
    return {
      expression: '* * * * * ?',
      locale: 'cn', // set 'cn' or 'en', default is 'cn'.
    }
  },
}
</script>
```
