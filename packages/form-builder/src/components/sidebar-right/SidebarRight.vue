<script setup lang="ts">
import { SidebarHeader } from "../ui/sidebar";
import type { SidebarProps } from "../ui/sidebar";
import { Sidebar, SidebarContent } from "../ui/sidebar";
import FormEditMain from "./FormEditMain.vue";
import { fieldProps } from "../../utils/field-props";
import { useFormField } from "../../composables/form-fields";

const { currentFieldType } = useFormField();

const props = withDefaults(defineProps<SidebarProps>(), {
  collapsible: "offcanvas",
  variant: "inset",
});
</script>

<template>
  <Sidebar v-bind="props" id="sidebar-right">
    <SidebarHeader>
      <div
        class="flex items-center w-fit gap-2 rounded-lg backdrop-blur-2xl"
      >
        <component
          :is="fieldProps.find((prop) => prop.name === currentFieldType)?.icon"
          class="!h-8 !w-8 rounded-md text-green-700 dark:text-white/70 bg-ring/20 p-1.5"
        />
      </div>
    </SidebarHeader>
    <SidebarContent>
      <FormEditMain />
    </SidebarContent>
  </Sidebar>
</template>
