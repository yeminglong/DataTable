<!--
 * @Author: yeminglong
 * @Date: 2025-03-13 04:20:40
 * @LastEd![这是图片](/assets/img/philly-magic-garden.jpg "Magic Gardens")itTime: 2025-03-13 04:52:11
 * @LastEditors: yeminglong
 * @Description:
-->

本组件是在element plus table的基础上封装的DataTable组件集成Table和pagination组件。所以支持Table和pagination所有的属性和事件。并且支持本地分页和格式化和jsx。

![效果图](./Snipaste_2025-03-13_04-48-31.png '效果图')

| 属性            | 描述             | 类型    | 默认值                                    |
| --------------- | ---------------- | ------- | ----------------------------------------- |
| layout          | 分页布局         | String  | 'total, sizes, prev, pager, next, jumper' |
| total           | 数据总数         | Number  | 0                                         |
| data            | 数据             | Array   |                                           |
| columns         | 列头             | Array   |                                           |
| pagination      | 是否分页         | Boolean | false                                     |
| localPagination | 是否启用本地分页 | Boolean | false                                     |
|                 |                  |         |                                           |
|                 |                  |         |                                           |
|                 |                  |         |                                           |

下面给是使用实例

```html
<template>
  <DataTable
    ref="tableRef"
    row-key="rowKey"
    :data="tableData"
    :total="24"
    pagination
    :columns="column"
    border
    v-model:page-no="current"
    v-model:page-size="pageSize"
    style="width: 100%; height: 100%"
    @sort-change="handleSortChange"
    sortable="custom"
    local-pagination
  >
  </DataTable>
</template>

<script setup lang="tsx">
  import _ from 'lodash'

  import { DataTable } from 'elementplus-data-table'
  import 'elementplus-data-table/index.css'

  const pageSize = ref(5)
  const current = ref(1)
  const tableData = ref([
    {
      id: '1bb3a5cd350d92e53b293e38960325c2',
      year: '2023',
      regionCode: '140000000',
      regionName: '山西省',
      useCount: '12',
      useWeight: '44'
    },
    {
      id: '459cfcac812e3eb7925f7eea5dca854e',
      year: '2023',
      regionCode: '140000000',
      regionName: '山西省',
      useCount: '12',
      useWeight: '44'
    },
    {
      id: '13ed9cea9fb532b2e7f976c5aeb4fb03',
      year: '2023',
      regionCode: '140100000',
      regionName: '太原市',
      useCount: '32',
      useWeight: '22'
    },
    {
      id: 'dcc55a13abcf745f03dc653f8ca82f21',
      year: '2023',
      regionCode: '140100000',
      regionName: '太原市',
      useCount: '32',
      useWeight: '22'
    },
    {
      id: '8c96cfe6230b63f43d00d1541a658a37',
      year: '2023',
      regionCode: '140200000',
      regionName: '大同市',
      useCount: '1',
      useWeight: '2'
    },
    {
      id: 'de625d632546ae3d74bd1df8f7d051ce',
      year: '2023',
      regionCode: '140200000',
      regionName: '大同市',
      useCount: '1',
      useWeight: '2'
    },
    {
      id: '5cc223cc809834de5a414f8c2ab0f074',
      year: '2023',
      regionCode: '140300000',
      regionName: '阳泉市',
      useCount: '23',
      useWeight: '4'
    },
    {
      id: '380097a831a9c57b74e5c7779442424a',
      year: '2023',
      regionCode: '140300000',
      regionName: '阳泉市',
      useCount: '23',
      useWeight: '4'
    },
    {
      id: '90777ab2cc04eeda2d9667246d025407',
      year: '2023',
      regionCode: '140400000',
      regionName: '长治市',
      useCount: '33',
      useWeight: '3'
    },
    {
      id: '84d3f0f88eba504933c47d3913f054cb',
      year: '2023',
      regionCode: '140400000',
      regionName: '长治市',
      useCount: '33',
      useWeight: '3'
    },
    {
      id: 'f1c1f9456f52945fc661153ca75b2388',
      year: '2023',
      regionCode: '140500000',
      regionName: '晋城市',
      useCount: '44',
      useWeight: '5'
    },
    {
      id: '6b498ba03ef9c2ed3cea43e4cee547eb',
      year: '2023',
      regionCode: '140500000',
      regionName: '晋城市',
      useCount: '44',
      useWeight: '5'
    },
    {
      id: '0963c7bff0d584bb7ade7aacf2ff9a8b',
      year: '2023',
      regionCode: '140600000',
      regionName: '朔州市',
      useCount: '22',
      useWeight: '5'
    },
    {
      id: '37e9b3f185fd81762c4dd74c2d0d7971',
      year: '2023',
      regionCode: '140600000',
      regionName: '朔州市',
      useCount: '22',
      useWeight: '5'
    },
    {
      id: 'd2fee1228d107bf418408535d6c4f447',
      year: '2023',
      regionCode: '140700000',
      regionName: '晋中市',
      useCount: '11',
      useWeight: '4'
    },
    {
      id: '0b5406e1af00bd1f62a784f18d9b259f',
      year: '2023',
      regionCode: '140700000',
      regionName: '晋中市',
      useCount: '11',
      useWeight: '4'
    },
    {
      id: '543cca57cd20e57ae0b6700f0f3908ee',
      year: '2023',
      regionCode: '140800000',
      regionName: '运城市',
      useCount: '343',
      useWeight: '5'
    },
    {
      id: '0cb1a2758bd2a65db37a3c09b46091f1',
      year: '2023',
      regionCode: '140800000',
      regionName: '运城市',
      useCount: '343',
      useWeight: '5'
    },
    {
      id: '4eb996e1455dc01cb7962ac91666a14f',
      year: '2023',
      regionCode: '140900000',
      regionName: '忻州市',
      useCount: '1',
      useWeight: '4'
    },
    {
      id: '639956044fc4062f5f7b10a8e0606054',
      year: '2023',
      regionCode: '140900000',
      regionName: '忻州市',
      useCount: '1',
      useWeight: '4'
    },
    {
      id: '30f8ab7a460066bee3dc52afe01c4558',
      year: '2023',
      regionCode: '141000000',
      regionName: '临汾市',
      useCount: '44',
      useWeight: '5'
    },
    {
      id: 'b0d72061168d6a50669260e5511574a8',
      year: '2023',
      regionCode: '141000000',
      regionName: '临汾市',
      useCount: '44',
      useWeight: '5'
    },
    {
      id: '9ab786c40df83099d6221bcebc433074',
      year: '2023',
      regionCode: '141100000',
      regionName: '吕梁市',
      useCount: null,
      useWeight: null
    },
    {
      id: 'dcd2da1bcaf88696437eb82d2b917118',
      year: '2023',
      regionCode: '141100000',
      regionName: '吕梁市',
      useCount: null,
      useWeight: null
    }
  ])

  for (const row of tableData.value) {
    row.rowKey = _.uniqueId()
  }

  const column = [
    { type: 'selection', reserveSelection: true, width: 55 },
    { type: 'index', width: 55, label: '序号' },
    { type: 'rowNumber', width: 55, label: '序号' },
    {
      label: '基础信息', // 顶层表头
      align: 'center',
      children: [
        {
          label: '年份',
          prop: 'year',
          align: 'center',
          showOverflowTooltip: true,
          width: 300,
          formatter: row => {
            return `${row.year}年${row.regionName}`
          },
          render: ({ row, value }) => {
            return <el-button>{row.id}</el-button>
            // return 123
          }
        },
        {
          label: '行政区划代码',
          prop: 'regionCode',
          align: 'center',
          showOverflowTooltip: true,
          render: ({ value, $index }) => {
            return (
              <el-button
                type='success'
                onClick={() => {
                  ElMessage({
                    type: 'success',
                    message: `${value}==${$index}`
                  })
                }}
              >
                {value}
              </el-button>
            )
            // return 123
          }
        }
      ]
    },
    {
      label: '排放数据', // 新增一个分组
      align: 'center',
      children: [
        {
          sortable: 'custom',
          label: '化学需氧量排放总量（吨）',
          prop: 'useCount',
          align: 'center',
          showOverflowTooltip: true
        },
        {
          sortable: 'custom',
          label: '工业源直接排放化学需氧量排放量（吨）',
          prop: 'useWeight',
          align: 'center',
          showOverflowTooltip: true
        }
      ]
    },
    {
      sortable: 'custom',
      label: '工业源直接排放化学需氧量排放量（吨）',
      prop: 'useWeight',
      align: 'center',
      showOverflowTooltip: true
    }
  ]

  const tableRef = ref()
  function getSelection() {
    const selection = tableRef.value?.getSelectionRows()
    alert(JSON.stringify(selection))
  }

  function handleSortChange({ column, prop, order }: any) {
    console.log(column, prop, order)
    const result = _.sortBy(tableData.value, item => {
      return isNaN(Number(item[prop])) ? 0 : Number(item[prop])
    })

    if (order === 'descending') {
      result.reverse()
    }

    console.log(JSON.stringify(result.map(item => item[prop])))
    tableData.value = result

    setTimeout(() => {
      tableData.value = result
    }, 20)
    // [order === 'ascending' ? 'asc' : 'desc'],
    // tableData.value.sort((a, b) => {
    //   let numA = Number(a[prop])
    //   let numB = Number(b[prop])
    //
    //   if (isNaN(numA)) {
    //     numA = 0
    //   }
    //   if (isNaN(numB)) {
    //     numB = 0
    //   }
    //   // return numB - numA
    //   return numA - numB
    // })
  }
</script>

<style scoped></style>
```
