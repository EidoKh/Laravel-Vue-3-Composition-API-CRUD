<template>
  <table class="items-center w-full bg-transparent border-collapse">
    <thead>
      <tr>
        <th
          class="
            px-4
            bg-gray-100
            dark:bg-gray-600
            text-gray-500
            dark:text-gray-100
            align-middle
            border border-solid border-gray-200
            dark:border-gray-500
            py-3
            text-xs
            uppercase
            border-l-0 border-r-0
            whitespace-nowrap
            font-semibold
            text-right
            min-w-140-px
          "
        >
          ت
        </th>
        <th
          v-for="column in columns"
          :key="column"
          class="
            px-4
            bg-gray-100
            dark:bg-gray-600
            text-gray-500
            dark:text-gray-100
            align-middle
            border border-solid border-gray-200
            dark:border-gray-500
            py-3
            text-xs
            uppercase
            border-l-0 border-r-0
            whitespace-nowrap
            font-semibold
            text-right
            min-w-140-px
          "
        >
          {{ column.label }}
        </th>
        <th
          class="
            px-4
            bg-gray-100
            dark:bg-gray-600
            text-gray-500
            dark:text-gray-100
            align-middle
            border border-solid border-gray-200
            dark:border-gray-500
            py-3
            text-xs
            uppercase
            border-l-0 border-r-0
            whitespace-nowrap
            font-semibold
            text-right
          "
        >
          عمليات
        </th>
      </tr>
    </thead>
    <tbody>
      <tr
        class="text-gray-700 dark:text-gray-100"
        v-for="row in rows"
        :key="row.id"
      >
        <td
          class="
            border-t-0
            px-4
            align-middle
            border-l-0 border-r-0
            text-xs
            whitespace-nowrap
            p-4
            text-right
          "
        >
          {{ row["id"] }}
        </td>
        <th
          v-for="column in columns"
          :key="column"
          class="
            border-t-0
            px-4
            align-middle
            border-l-0 border-r-0
            text-xs
            whitespace-nowrap
            p-4
            text-right
          "
        >
          {{ row[column.column] }}
        </th>
        <th
          class="
            border-t-0
            px-4
            align-middle
            border-l-0 border-r-0
            text-xs
            whitespace-nowrap
            p-4
            text-right
            flex
          "
        >
          <span class="cursor-pointer" @click="$emit('delete', row['id'])"
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-5 text-red-500"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
              /></svg
          ></span>
          <span class="cursor-pointer" @click="$emit('edit', row['id'])"
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-5 text-indigo-300"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
              /></svg
          ></span>
          <span class="cursor-pointer" @click="$emit('view', row['id'])"
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              class="
                h-6
                w-6
                cursor-pointer
                view
                is-rows-el
                quick-btn
                text-blue-400
              "
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"
              />
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"
              /></svg
          ></span>
        </th>
      </tr>
    </tbody>
  </table>
</template>
<script>
import { onMounted } from "@vue/runtime-core";
export default {
  emits: ["delete", "edit", "view"],
  props: {
    columns: Array,
    rows: Array,
  },
  setup(props) {
    onMounted(() => {});
    return {};
  },
};
</script>