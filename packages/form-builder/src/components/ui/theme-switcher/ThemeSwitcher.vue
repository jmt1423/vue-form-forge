<script setup lang="ts">
import { Button } from "../button";
import {
  DropdownMenu,
  DropdownMenuContent,
  DropdownMenuItem,
  DropdownMenuTrigger,
} from "../dropdown-menu";
import { useColorMode } from "@vueuse/core";
import { Sun, Moon } from "lucide-vue-next";

const colorModeOptions = {
  disableTransition: false,
};
const mode = useColorMode(colorModeOptions);
</script>

<template>
  <DropdownMenu>
    <DropdownMenuTrigger as-child>
      <Button variant="secondary" class="h-6 w-6 !p-3">
        <Sun
          class="h-3 w-3 rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0 dark:text-green-200"
        />
        <Moon
          class="absolute h-3 w-3 rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100 dark:text-green-200"
        />
        <span class="sr-only">Toggle theme</span>
      </Button>
    </DropdownMenuTrigger>
    <DropdownMenuContent align="end" class="">
      <DropdownMenuItem @click="mode = 'light'"> Light </DropdownMenuItem>
      <DropdownMenuItem @click="mode = 'dark'"> Dark </DropdownMenuItem>
      <DropdownMenuItem @click="mode = 'auto'"> System </DropdownMenuItem>
    </DropdownMenuContent>
  </DropdownMenu>
</template>