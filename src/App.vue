<template>
  <main class="h-screen w-screen bg-purple-500 p-10">
    <div class="rounded-md p-5 shadow-lg bg-white max-w-xl mx-auto">
      <span
        :ref="listbox.label.ref"
      >
        Select a wrestler:
      </span>
      <button
        :ref="listbox.button.ref"
        class="rounded p-3 border"
      >
        {{ listbox.selected }}
      </button>
      <ul
        :ref="listbox.list.ref"
        v-show="listbox.list.isOpen"
      >
        <li
          v-for="({ value, isActive, isSelected }) in listbox.options.values"
          :key="value"
          :ref="listbox.options.ref"
        >
          <div 
            class="p-3" 
            :class="isActive ? 'bg-blue-600 text-white' : 'bg-white text-gray-900'"
          >
            {{ value }}
            <!-- Heroicons checkmark -->
            <svg
              v-show="isSelected"
              viewBox="0 0 20 20"
              fill="currentColor"
              class="ml-2 inline check w-6 h-6"
            >
              <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path>
            </svg>
          </div>
        </li>
      </ul>
    </div>
  </main>
</template>

<script>
import { reactive } from 'vue'
import useListbox from '@tailwindui/vue/src/useListbox'

export default {
  setup () {
    const listbox = useListbox({
            options: [
              'The Ultimate Warrior',
              'Randy Savage',
              'Hulk Hogan',
              'Bret Hart',
              'The Undertaker',
              'Mr. Perfect',
              'Ted DiBiase',
              'Bam Bam Bigelow',
              'Yokozuna',
            ],
            defaultOption: 'The Ultimate Warrior'
          })
  
    return {
      listbox: reactive(listbox),
    }
  }      
}
</script>
