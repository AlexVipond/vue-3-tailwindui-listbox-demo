<template>
  <div>
    <span
      :ref="listbox.label.ref"
    >
      Select a wrestler:
    </span>
    <button
      :ref="listbox.button.ref"
      class="rounded p-3 border"
    >
      {{ listbox.selected.value }}
    </button>
    <ul
      :ref="listbox.list.ref"
      v-show="listbox.list.isOpen.value"
    >
      <li
        v-for="({ value, isActive, isSelected }) in listbox.options.values"
        :key="value"
        :ref="listbox.options.ref"
      >
        <div 
          class="p-3" 
          :class="isActive.value ? 'bg-blue-600 text-white' : 'bg-white text-gray-900'"
        >
          {{ value }}
          {{ isSelected.value }}
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
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
      listbox,
    }
  }      
}
</script>
