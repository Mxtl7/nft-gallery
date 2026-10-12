<template>
  <ColorScheme>
    <KIcon
      class="cursor-pointer md:hidden"
      :name="currentMode.icon"
      size="medium"
      @click="switchToNextMode"
    />
    <NeoDropdown
      v-model="preference"
      class="max-md:hidden"
      position="top-right"
      :close-on-click="true"
      aria-role="list"
      @change="onChange"
    >
      <template #trigger>
        <div class="flex items-center cursor-pointer">
          <KIcon
            :name="currentMode.icon"
            size="medium"
          />
          <span class="ml-1 min-w-[82px]">{{ currentMode?.label }}</span>
        </div>
      </template>
      <NeoDropdownItem
        v-for="option in options"
        :key="option.value"
        aria-role="listitem"
        class="flex"
        :active="preference === option.value"
        :value="option"
      >
        <KIcon
          class="mr-2"
          :name="option.icon"
        />
        <span>{{ option.label }}</span>
      </NeoDropdownItem>
    </NeoDropdown>
  </ColorScheme>
</template>

<script lang="ts" setup>
import { NeoDropdown, NeoDropdownItem } from '@kodadot1/brick'

const {
  preference,
  setColorMode,
  themeOptions: options,
  currentMode,
  switchToNextMode,
} = useTheme()

const onChange = (option) => {
  setColorMode(option.value)
}
</script>
