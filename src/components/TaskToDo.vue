<script setup lang="ts">
import { ref } from 'vue'
interface Item {
  name: string
  condition: boolean
}
const items = ref<Item[]>([])
const newItemName = ref('')
const newCondition = ref(false)
const addItem = () => {
  if (newItemName.value === ''){
    newItemName.value = ''
  }
  else{
  items.value.push({ name: newItemName.value , condition: newCondition.value})
  newItemName.value = ''}
}
</script>

<template>
  <div>
    <div>ItemList</div>
    <ul>
      <div v-for="item in items" :key="item.name" class="place">
        <li v-if="item.condition === false" class="false">
          <div>タスク: {{  item.name  }}</div>
          <div>状態：<button @click="item.condition = true">{{ item.condition ? '完了' : '未完了' }}</button></div>
        </li>
        <li v-if="item.condition === true" class="true">タスク "{{ item.name }}" - {{ item.condition ? '完了' : '未完了' }}
        </li>
      </div>
    </ul>
    <div>
      <label>
        タスク
        <input v-model="newItemName" type="text" />
      </label>
      <button @click="addItem">追加</button>
    </div>
  </div>
</template>

<style>
</style>