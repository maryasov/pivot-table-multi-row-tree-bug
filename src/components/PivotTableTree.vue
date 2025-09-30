<template>
  <PivotTable :options="tableOptions" />
</template>

<script setup>
import { ref, onMounted } from "vue";
import { PivotTable } from "@visactor/vue-vtable";

const tableOptions = ref({});
console.log(tableOptions);

onMounted(() => {
  fetch(
    "https://raw.githubusercontent.com/maryasov/pivot-table-multi-row-tree-test/refs/heads/main/demo-data.json"
  )
    .then((res) => res.json())
    .then((data) => {
      tableOptions.value = {
        records: data,

        rows: [
          {
            dimensionKey: "Department@0",
            title: "Department",
            width: "auto",
          },
          {
            dimensionKey: "Department@1",
            width: "auto",
          },
        ],

        // ExtensionRows
        extensionRows: [
          {
            rows: [
              {
                dimensionKey: "Product@0",
                title: "Product",
                width: "auto",
              },
              {
                dimensionKey: "Product@1",
                width: "auto",
              },
              {
                dimensionKey: "Product@2",
                width: "auto",
              },
            ],
            rowTree: [
              {
                dimensionKey: "Product@0",
                value: "All",
                hierarchyState: "expand",
                children: [
                  {
                    dimensionKey: "Product@1",
                    value: "Gadgets",
                    hierarchyState: "expand",
                    children: [
                      {
                        dimensionKey: "Product@2",
                        value: "Smartphone",
                      },
                      {
                        dimensionKey: "Product@2",
                        value: "Laptop",
                      },
                    ],
                  },
                  {
                    dimensionKey: "Product@1",
                    value: "Kitchen",
                    hierarchyState: "expand",
                    children: [
                      {
                        dimensionKey: "Product@2",
                        value: "Teapot",
                      },
                      {
                        dimensionKey: "Product@2",
                        value: "Microwave",
                      },
                    ],
                  },
                ],
              },
            ],
          },
          {
            rows: [
              {
                dimensionKey: "Version@0",
                title: "Version",
                width: "auto",
              },
            ],
            rowTree: [
              {
                dimensionKey: "Version@0",
                value: "Plan",
              },
              {
                dimensionKey: "Version@0",
                value: "Act",
              },
            ],
          },
        ],

        rowTree: [
          {
            dimensionKey: "Department@0",
            value: "Msk",
            hierarchyState: "expand",
            children: [
              {
                dimensionKey: "Department@1",
                value: "Sales",
              },
              {
                dimensionKey: "Department@1",
                value: "Production",
              },
            ],
          },
          {
            dimensionKey: "Department@0",
            value: "Spb",
            hierarchyState: "expand",
            children: [
              {
                dimensionKey: "Department@1",
                value: "Sales",
              },
              {
                dimensionKey: "Department@1",
                value: "Production",
              },
            ],
          },
        ],

        columns: [
          {
            dimensionKey: "Period@0",
            title: "Period",
            width: "auto",
            headerStyle: { textStick: true },
          },
          {
            dimensionKey: "Period@1",
            width: "auto",
            headerStyle: { textStick: true },
          },
          {
            dimensionKey: "Scenario@0",
            title: "Scenario",
            width: "auto",
            headerStyle: { textStick: true },
          },
        ],

        columnTree: [
          {
            dimensionKey: "Period@0",
            value: "2025",
            children: [
              {
                dimensionKey: "Scenario@0",
                value: "Baseline",
              },
              {
                dimensionKey: "Scenario@0",
                value: "Negative",
              },
              {
                dimensionKey: "Period@1",
                value: "Jan 2025",
                children: [
                  {
                    dimensionKey: "Scenario@0",
                    value: "Baseline",
                  },
                  {
                    dimensionKey: "Scenario@0",
                    value: "Negative",
                  },
                ],
              },
              {
                dimensionKey: "Period@1",
                value: "Feb 2025",
                children: [
                  {
                    dimensionKey: "Scenario@0",
                    value: "Baseline",
                  },
                  {
                    dimensionKey: "Scenario@0",
                    value: "Negative",
                  },
                ],
              },
            ],
          },
          {
            dimensionKey: "Period@0",
            value: "2026",
            children: [
              {
                dimensionKey: "Scenario@0",
                value: "Baseline",
              },
              {
                dimensionKey: "Scenario@0",
                value: "Negative",
              },
              {
                dimensionKey: "Period@1",
                value: "Jan 2026",
                children: [
                  {
                    dimensionKey: "Scenario@0",
                    value: "Baseline",
                  },
                  {
                    dimensionKey: "Scenario@0",
                    value: "Negative",
                  },
                ],
              },
              {
                dimensionKey: "Period@1",
                value: "Feb 2026",
                children: [
                  {
                    dimensionKey: "Scenario@0",
                    value: "Baseline",
                  },
                  {
                    dimensionKey: "Scenario@0",
                    value: "Negative",
                  },
                ],
              },
            ],
          },
        ],

        indicators: [
          {
            indicatorKey: "Value",
            title: "Значение",
            width: 120,
            showSort: false,
            headerStyle: { fontWeight: "normal" },
          },
        ],

        corner: {
          titleOnDimension: "row",
          headerStyle: { textStick: true },
        },

        columnHierarchyType: "grid-tree",
        columnExpandLevel: 99,
        hideIndicatorName: true,
        rowHierarchyType: "tree",
        rowHierarchyIndent: 10,
        rowExpandLevel: 99,
        rowHierarchyTextStartAlignment: true,

        widthMode: "standard",
        defaultRowHeight: 20,
        defaultColWidth: 40,
      };
    });
});
</script>
