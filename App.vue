<script setup>
import { Button, Badge, Alert, TextInput, Sidebar, ListView, Avatar, Breadcrumbs, AxisChart, DonutChart, FunnelChart, NumberChart } from './src'
import { ref } from 'vue'

const isDark = ref(false)

function toggleTheme() {
  isDark.value = !isDark.value
  document.documentElement.setAttribute(
    'data-theme',
    isDark.value ? 'dark' : 'light'
  )
}

const sections = ref([
  {
    label: 'Main',
    items: [
      { label: 'Home', suffix: '8', isActive: true, onClick: () => setActive('Home') },
      { label: 'User', suffix: '4', isActive: false, onClick: () => setActive('User') },
      { label: 'Notification', isActive: false, onClick: () => setActive('Notification') },
    ],
  },
  {
    label: 'Finance',
    collapsible: true,
    items: [
      { label: 'Invoice', suffix: '8', isActive: false, onClick: () => setActive('Invoice') },
      { label: 'Payments', suffix: '8', isActive: false, onClick: () => setActive('Payments') },
    ],
  },
])

function setActive(label) {
  sections.value.forEach(section => {
    section.items.forEach(item => {
      item.isActive = item.label === label
    })
  })
}

const columns = ref([
  { label: 'Name', key: 'name', width: '200px' },
  { label: 'Email', key: 'email', width: '220px' },
  { label: 'Role', key: 'role', width: '150px' },
  { label: 'Status', key: 'status', width: '120px' },
])

const rows = ref([
  { id: 1, name: 'John Doe', email: 'john@doe.com', role: 'Developer', status: 'Active' },
  { id: 2, name: 'Jane Smith', email: 'jane@smith.com', role: 'Designer', status: 'Active' },
  { id: 3, name: 'Bob Wilson', email: 'bob@wilson.com', role: 'Manager', status: 'Inactive' },
  { id: 4, name: 'Alice Brown', email: 'alice@brown.com', role: 'Developer', status: 'Active' },
  { id: 5, name: 'Charlie Davis', email: 'charlie@davis.com', role: 'Designer', status: 'Active' },
])

const subtleValue = ref('')
const outlineValue = ref('')
const prefixValue = ref('')
const suffixValue = ref('')
const ghostValue = ref('')
</script>

<template>
  <div
    style="display: flex; height: 100vh; font-family: Avenir, sans-serif;"
    :data-theme="isDark ? 'dark' : 'light'"
  >
    <Sidebar
      :header="{ title: 'Intrakore', subtitle: 'admin@intrakore.com' }"
      :sections="sections"
    />

    <div style="flex: 1; overflow-y: auto; padding: 40px; display: flex; flex-direction: column; gap: 32px; background: var(--surface-white);">

      <!-- Header -->
      <div style="display: flex; justify-content: space-between; align-items: center;">
        <h1 style="font-size: 28px; font-weight: 900; font-family: 'ITC Avant Garde Gothic Pro'; color: var(--text-ink-gray-9);">
          Intrakore Design Preview
        </h1>
        <button
          @click="toggleTheme"
          style="padding: 8px 20px; border-radius: 6px; background: #000FCC; color: white; border: none; cursor: pointer; font-family: Avenir, sans-serif;"
        >
          {{ isDark ? '☀️ Light Mode' : '🌙 Dark Mode' }}
        </button>
      </div>

      <!-- Buttons — Blueprint -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">BUTTONS — BLUEPRINT</p>
        <div style="display: flex; gap: 12px; flex-wrap: wrap;">
          <Button variant="solid" theme="blueprint">Solid</Button>
          <Button variant="subtle" theme="blueprint">Subtle</Button>
          <Button variant="outline" theme="blueprint">Outline</Button>
          <Button variant="ghost" theme="blueprint">Ghost</Button>
          <Button variant="solid" theme="blueprint" :disabled="true">Disabled</Button>
          <Button variant="solid" theme="blueprint" :loading="true">Loading</Button>
        </div>
      </div>

      <!-- Buttons — Gray -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">BUTTONS — GRAY</p>
        <div style="display: flex; gap: 12px; flex-wrap: wrap;">
          <Button variant="solid" theme="gray">Solid</Button>
          <Button variant="subtle" theme="gray">Subtle</Button>
          <Button variant="outline" theme="gray">Outline</Button>
          <Button variant="ghost" theme="gray">Ghost</Button>
          <Button variant="solid" theme="gray" :disabled="true">Disabled</Button>
        </div>
      </div>

      <!-- List View -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">LIST VIEW</p>
        <ListView
          :columns="columns"
          :rows="rows"
          row-key="id"
          :options="{ selectable: true, showTooltip: true }"
        />
      </div>

      <!-- Badges -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">BADGES</p>
        <div style="display: flex; gap: 12px; flex-wrap: wrap;">
          <Badge theme="blue">Blueprint</Badge>
          <Badge theme="gray">Neutral</Badge>
          <Badge theme="red">Error</Badge>
          <Badge theme="green">Success</Badge>
        </div>
      </div>

      <!-- Alerts -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">ALERTS</p>
        <div style="display: flex; flex-direction: column; gap: 12px;">
          <Alert title="Blueprint Info" theme="blue" variant="subtle">Blueprint info state</Alert>
          <Alert title="Success State" theme="green" variant="subtle">Clearing green for success</Alert>
          <Alert title="Warning State" theme="yellow" variant="subtle">Amber for warnings</Alert>
          <Alert title="Error State" theme="red" variant="subtle">Red for errors</Alert>
        </div>
      </div>

      <!-- Text Input — Subtle -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">TEXT INPUT — SUBTLE</p>
        <div style="display: flex; flex-direction: column; gap: 12px; max-width: 400px;">
          <TextInput
            variant="subtle"
            size="sm"
            placeholder="Default (sm)"
            v-model="subtleValue"
          />
          <TextInput
            variant="subtle"
            size="md"
            placeholder="Default (md)"
            v-model="subtleValue"
          />
          <TextInput
            variant="subtle"
            size="lg"
            placeholder="Default (lg)"
            v-model="subtleValue"
          />
          <TextInput
            variant="subtle"
            size="sm"
            placeholder="Disabled"
            :disabled="true"
          />
        </div>
      </div>

      <!-- Text Input — Outline -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">TEXT INPUT — OUTLINE</p>
        <div style="display: flex; flex-direction: column; gap: 12px; max-width: 400px;">
          <TextInput
            variant="outline"
            size="sm"
            placeholder="Default (sm)"
            v-model="outlineValue"
          />
          <TextInput
            variant="outline"
            size="md"
            placeholder="Default (md)"
            v-model="outlineValue"
          />
          <TextInput
            variant="outline"
            size="lg"
            placeholder="Default (lg)"
            v-model="outlineValue"
          />
          <TextInput
            variant="outline"
            size="sm"
            placeholder="Disabled"
            :disabled="true"
          />
        </div>
      </div>

      <!-- Text Input — Prefix / Suffix -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">TEXT INPUT — PREFIX / SUFFIX</p>
        <div style="display: flex; flex-direction: column; gap: 12px; max-width: 400px;">
          <TextInput
            variant="subtle"
            size="md"
            placeholder="Search..."
            v-model="prefixValue"
          >
            <template #prefix>
              <svg style="width:16px;height:16px;" viewBox="0 0 16 16" fill="none">
                <circle cx="7" cy="7" r="4.5" stroke="currentColor" stroke-width="1.5"/>
                <path d="M10.5 10.5L13 13" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
              </svg>
            </template>
          </TextInput>
          <TextInput
            variant="outline"
            size="md"
            placeholder="Enter email"
            v-model="suffixValue"
          >
            <template #suffix>
              <svg style="width:16px;height:16px;" viewBox="0 0 16 16" fill="none">
                <rect x="2" y="4" width="12" height="9" rx="1.5" stroke="currentColor" stroke-width="1.5"/>
                <path d="M2 6l6 4 6-4" stroke="currentColor" stroke-width="1.5"/>
              </svg>
            </template>
          </TextInput>
        </div>
      </div>

      <!-- Text Input — Ghost -->
      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">TEXT INPUT — GHOST</p>
        <div style="display: flex; flex-direction: column; gap: 12px; max-width: 400px;">
          <TextInput
            variant="ghost"
            size="md"
            placeholder="Ghost — no chrome"
            v-model="ghostValue"
          />
        </div>
      </div>

  <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">BADGES — BLUEPRINT</p>
        <div style="display: flex; gap: 12px; flex-wrap: wrap;">
          <Badge theme="blueprint" variant="subtle">Subtle</Badge>
          <Badge theme="blueprint" variant="solid">Solid</Badge>
          <Badge theme="blueprint" variant="outline">Outline</Badge>
          <Badge theme="blueprint" variant="ghost">Ghost</Badge>
        </div>
      </div>

      <div>
        <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">AVATAR</p>
        <div style="display: flex; gap: 12px; align-items: center; flex-wrap: wrap;">
          <Avatar size="xs" label="Shaistha" />
          <Avatar size="sm" label="Shaistha" />
          <Avatar size="md" label="Shaistha" />
          <Avatar size="lg" label="Shaistha" />
          <Avatar size="xl" label="Shaistha" />
          <Avatar size="2xl" label="Shaistha" />
          <Avatar size="3xl" label="Shaistha" />
        </div>
        <div style="display: flex; gap: 12px; align-items: center; flex-wrap: wrap; margin-top: 12px;">
          <Avatar size="md" shape="square" label="Shaistha" />
          <Avatar size="xl" shape="square" label="Shaistha" />
          <Avatar size="2xl" shape="square" label="Shaistha" />
          <Avatar size="2xl" label="Shaistha" image="https://avatars.githubusercontent.com/u/9355208" />
        </div>
      </div>
      <div>
  <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-8);">BREADCRUMBS</p>
  <Breadcrumbs
    :items="[
      { label: 'Home', route: '/' },
      { label: 'Projects', route: '/' },
      { label: 'Intrakore ERP' },
    ]"
  />
</div>
<!-- Number Chart -->
<div>
  <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-5);">NUMBER CHART</p>
  <div style="display: flex; gap: 12px; flex-wrap: wrap;">
    <NumberChart :config="{
      title: 'Total Revenue',
      value: 1250000,
      prefix: 'AED',
      delta: 12.5,
      deltaPrefix: '+',
      deltaSuffix: '%'
    }" style="width: 200px; border: 1px solid var(--outline-gray-2); border-radius: 8px;" />
    <NumberChart :config="{
      title: 'Lost Deals',
      value: 45000,
      prefix: 'AED',
      delta: -5.2,
      deltaSuffix: '%'
    }" style="width: 200px; border: 1px solid var(--outline-gray-2); border-radius: 8px;" />
  </div>
</div>

<!-- Axis Chart -->
<div>
  <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-8);">AXIS CHART</p>
  <AxisChart :config="{
    title: 'Monthly Revenue',
    colors: ['#000FCE', '#705CFF', '#68C2A3'],
    xAxis: { key: 'month', type: 'category' },
    yAxis: { title: 'Revenue' },
    series: [{ name: 'revenue', type: 'bar' }],
    data: [
      { month: 'Jan', revenue: 120000 },
      { month: 'Feb', revenue: 180000 },
      { month: 'Mar', revenue: 150000 },
      { month: 'Apr', revenue: 210000 },
      { month: 'May', revenue: 190000 },
      { month: 'Jun', revenue: 240000 },
    ]
  }" style="height: 300px;" />
</div>

<!-- Donut Chart -->
<div>
  <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-8);">DONUT CHART</p>
  <DonutChart :config="{
    title: 'Deal Status',
    colors: ['#000FCE', '#705CFF', '#68C2A3', '#8D95F6'],
    categoryColumn: 'status',
    valueColumn: 'count',
    data: [
      { status: 'Won', count: 45 },
      { status: 'Lost', count: 20 },
      { status: 'Active', count: 30 },
      { status: 'Pending', count: 5 },
    ]
  }" style="height: 300px;" />
</div>

<!-- Funnel Chart -->
<div>
  <p style="font-size: 12px; margin-bottom: 12px; color: var(--text-ink-gray-8);">FUNNEL CHART</p>
  <FunnelChart :config="{
    title: 'Sales Pipeline',
    categoryColumn: 'stage',
    valueColumn: 'count',
    data: [
      { stage: 'Leads', count: 100 },
      { stage: 'Qualified', count: 75 },
      { stage: 'Proposal', count: 50 },
      { stage: 'Negotiation', count: 30 },
      { stage: 'Won', count: 15 },
    ]
  }" style="height: 300px;" />
</div>

    </div>
  </div>
</template>