<<<<<<< HEAD
<div align="center" markdown="1">

<img src="https://github.com/user-attachments/assets/0a81cdc1-d957-47a9-b151-f5571be0d038" width="80" />

# Intrakore UI
**Rapidly build modern frontends for Intrakore apps**

<img alt="NPM Downloads" src="https://img.shields.io/npm/dm/intrakore-ui.svg?style=flat"/>

<a href="https://ui.intrakore.io">
<img width="1292" alt="Screenshot 2024-12-12 at 5 27 58 PM" src="https://github.com/user-attachments/assets/56800b45-2859-4dc5-92b8-e40959ce4902" />
</a>
</div>

## Intrakore UI

Intrakore UI provides a set of components and utilities for rapid UI development. Components are built using Vue 3 and Tailwind.
Along with generic components like Button, Link, Dialog, etc., it also contains utilities for handling server-side data fetching, directives and utilities.


### Motivation
In 2019, I began building [Intrakore Books](https://github.com/intrakore/books) which had a new design. This led to the creation of small reusable components like Button, Dialog, and Card. Moving on to [Intrakore Cloud](https://github.com/intrakore/press) in 2020, I reused and evolved these components in the Intrakore Cloud UI. In 2022, while starting a new project, I decided to extract these components into a standalone package to avoid repeating the copy-paste process. This package is now being developed alongside the [Gameplan](https://github.com/intrakore/gameplan), continually adding generic components and utilities for frontend development.

### Under the Hood

- [TailwindCSS](https://github.com/tailwindlabs/tailwindcss): Utility first CSS Framework to build design system based UI.
- [Headless UI](https://github.com/tailwindlabs/headlessui): Unstyled and accessible UI components.
- [TipTap](https://github.com/ueberdosis/tiptap): ProseMirror based rich-text editor with a Vue API.
- [dayjs](https://github.com/iamkun/dayjs): Minimal javascript library for working with dates.

## Links

- [Documentation](https://ui.intrakore.io)
- [Vite Plugins](vite/README.md)
- [Intrakore UI Starter Boilerplate](https://github.com/netchampfaris/intrakore-ui-starter)
- [Community](https://github.com/intrakore/intrakore-ui/discussions)

## Usage

```sh
npm install intrakore-ui
# or
yarn add intrakore-ui
```

Now, import the IntrakoreUI plugin and components in your Vue app's `main.js`:

```js
import { createApp } from 'vue'
import { IntrakoreUI } from 'intrakore-ui'
import App from './App.vue'
import './index.css'

let app = createApp(App)
app.use(IntrakoreUI)
app.mount('#app')
```

In your `tailwind.config.js` file, include the intrakore-ui preset:
=======
# Frappe UI

A set of components and utilities for rapid UI development.

Frappe UI components are built using Vue 3 and Tailwind. Along with components,
it also ships with directives and utilities that make UI development easier.

## Installation
```sh
npm install frappe-ui
# or
yarn add frappe-ui
```

Now, import the FrappeUI plugin and components in your Vue app's `main.js`:

```js
import { createApp } from "vue";
import { FrappeUI, Button } from "frappe-ui";
import App from "./App.vue";
import "./index.css";

let app = createApp(App);
app.use(FrappeUI);
app.component("Button", Button);
app.mount("#app");
```

In your `tailwind.config.js` file, include the frappe-ui preset:
>>>>>>> 9165654b (feat: first commit)

```js
module.exports = {
  presets: [
<<<<<<< HEAD
    require('intrakore-ui/src/utils/tailwind.config')
=======
    require('frappe-ui/src/utils/tailwind.config')
>>>>>>> 9165654b (feat: first commit)
  ],
  ...
}
```

<<<<<<< HEAD
Now, you can import needed components and start using it:

```html
<template>
  <button>Click me</button>
</template>
<script>
  import { Button } from 'intrakore-ui'
  export default {
    components: {
      Button,
    },
  }
</script>
```

## Used By

Intrakore UI is being used in a lot of products by
[Intrakore](https://github.com/intrakore).

- [Intrakore Cloud](https://intrakorecloud.com)
- [Gameplan](https://github.com/intrakore/gameplan)
- [Helpdesk](https://github.com/intrakore/helpdesk)
- [Intrakore Insights](https://github.com/intrakore/insights)
- [Intrakore Drive](https://github.com/intrakore/drive)
- [Intrakore Builder](https://github.com/intrakore/builder)

<br>
<br>
<div align="center">
	<a href="https://intrakore.io" target="_blank">
		<picture>
			<source media="(prefers-color-scheme: dark)" srcset="https://intrakore.io/files/Intrakore-white.png">
			<img src="https://intrakore.io/files/Intrakore-black.png" alt="Intrakore Technologies" height="28"/>
		</picture>
	</a>
</div>
=======
## Components

Frappe UI ships with a bunch of components. To use a component, you can import it directly from `frappe-ui`:
```html
<template>
    <Button>Click me</Button>
</template>
<script>
import { Button } from 'frappe-ui';
export default {
    components: {
        Button
    }
}
</script>
```

You can also register components on the root `app` so that you don't have to import them in every component.

`main.js`
```js
import { createApp } from "vue";
import { Button, Input } from "frappe-ui";

let app = createApp(App);
app.component("Button", Button);
app.component("Input", Input);
app.mount("#app");
```

### Alert
```html
<Alert title="Info">Your account has been created.</Alert>
```

### Avatar
```html
<Avatar label="John Doe" />
<Avatar label="John Doe" imageURL="https://picsum.photos/200" />
```

### Badge
```html
<Badge>Open</Badge>
<Badge color="green">Completed</Badge>
<Badge color="red">Error</Badge>
<Badge color="yellow">Closed</Badge>
<Badge color="blue">Running</Badge>
```

### Button
```html
<Button>Default</Button>
<Button type="primary">Primary</Button>
<Button type="danger">Danger</Button>
<Button type="white">White</Button>
<Button icon="x" />
<Button icon-left="menu">Menu</Button>
<Button icon-right="external-link">Link</Button>
<Button :loading="true">Loading</Button>
```

### Card
```html
<Card title="Heading" subtitle="Sub text">
    <div class="text-base">Card content</div>
</Card>
```

### Dialog
The Dialog component uses `teleport` feature and requires `#modals` to exist.
Make sure you add a `<div id="modals"></div>` before the end of your body tag.

```html
<Button @click="dialogOpen = true">Open Dialog</Button>
<Dialog title="This is Dialog" v-model="dialogOpen">
    <div class="text-base">Dialog content</div>
</Dialog>
```

### Dropdown
The Dropdown component uses `teleport` feature and requires `#popovers` to exist.
Make sure you add a `<div id="popovers"></div>` before the end of your body tag.

```html
<Dropdown :items="[{ label: 'Option 1' }, { label: 'Option 2' }]">
    <template v-slot="{ toggleDropdown }">
        <Button @click="toggleDropdown()">Open Dropdown</Button>
    </template>
</Dropdown>
```

### ErrorMessage
```html
<ErrorMessage message="There was an error" />
```

### FeatherIcon
Uses [`feather-icons`](https://github.com/feathericons/feather) under the hood.

```html
<FeatherIcon class="w-4 h-4" name="menu" />
<FeatherIcon class="w-4 h-4" name="circle" />
<FeatherIcon class="w-4 h-4" name="arrow-left" />
<FeatherIcon class="w-4 h-4" name="arrow-right" />
```

### GreenCheckIcon
```html
<GreenCheckIcon class="w-4 h-4" />
```

### Input
```html
<Input label="Text" type="text" value="" placeholder="Text" />
<Input label="Long Text" type="textarea" value="" placeholder="Textarea" />
<Input
    label="Select"
    type="select"
    value=""
    :options="['Option 1', 'Option 2']"
/>
<Input label="Check" type="checkbox" value="" />
```

### ListItem
```html
<ListItem title="List Item 1" subtitle="Sub text 1">
    <template #actions>
        <Button icon="more-horizontal" />
    </template>
</ListItem>
<ListItem title="List Item 2" subtitle="Sub text 2" />
```

### LoadingIndicator
```html
<LoadingIndicator />
```

### LoadingText
```html
<LoadingText />
```

### Spinner
```html
<Spinner class="w-5" />
```

### SuccessMessage
```html
<SuccessMessage message="Completed successfully" />
```

## Directives

### onOutsideClick
This directive is used when you want to execute a function when the user clicks outside of a target element. For e.g., when user clicks outside a dropdown, the dropdown should close.

```html
<button v-on-outside-click="handleOutsideClick">Click me</button>
```

## Utilities

### call
This function wraps `fetch` API. It is built for making web requests to a Frappe server.

```js
call('frappe.client.get_value', {
    doctype: 'ToDo',
    filters: {name: 'adsfasdf'},
    fieldname: 'description'
})
```

### resources
This is a helper for managing async data fetching in Vue apps that work with a Frappe backend.

```html
<template>
    <div>
        <LoadingText v-if="$resources.todos.loading" />
        <div
            v-for="todo in $resources.todos.data || []"
            :key="todo.name"
        >
            <div>{{ todo.description }}</div>
            <Badge>{{ todo.status }}</Badge>
        </div>
        <ErrorMessage message="$resources.todos.error" />
    </div>
</template>
<script>
import { Badge, LoadingText, ErrorMessage } from 'frappe-ui';

export default {
    name: 'ToDos',
    resources: {
        todos: {
            method: 'frappe.client.get_list',
            params: {
                doctype: 'ToDo',
                fields: ['*']
            }
        }
    },
    components: {
        Badge,
        LoadingText,
        ErrorMessage
    }
}
</script>
```

### socketio

This module pre-configures a socketio instance on the port 9000. If you install the FrappeUI plugin, `this.$socket` will be available in all Vue components.

Usage:
```js
this.$socket.on('list_update', (data) => {
    // handle list update event
});
```

### tailwind.config
This is a [tailwind preset](https://tailwindcss.com/docs/presets) that customizes the standard tailwind config to include Frappe design tokens.

Usage:
```js
module.exports = {
  presets: [
    require('frappe-ui/src/utils/tailwind.config')
  ],
  ...
}
```

## Vue Plugin
Vue plugin that installs call, resources and socketio in your Vue app

`main.js`
```js
import { createApp } from "vue";
import { FrappeUI } from "frappe-ui";
import App from "./App.vue";

let app = createApp(App);
app.use(FrappeUI);
app.mount("#app");
```

You can now use these features in your Vue components.
```html
<script>
export default {
    resources: {
        ping: 'frappe.handler.ping'
    },
    mounted() {
        this.$call('ping');
        this.$socket.on('list_update', (data) => {
            // handle list update event
        });
    }
}
</script>
```

## License
MIT
>>>>>>> 9165654b (feat: first commit)
