<!--
 * @Author: yeminglong
 * @Date: 2025-03-13 04:20:40
 * @LastEd![这是图片](/assets/img/philly-magic-garden.jpg "Magic Gardens")itTime: 2025-03-13 04:52:11
 * @LastEditors: yeminglong
 * @Description:
-->

本组件是在element plus table的基础上封装的DataTable组件集成Table和pagination组件。所以支持Table和pagination所有的属性和事件。并且支持本地分页和格式化和jsx。

![效果图](./Snipaste_2025-03-13_04-48-31.png '效果图')

| 属性            | 描述                   | 类型     | 默认值                                    |
| --------------- | ---------------------- | -------- | ----------------------------------------- |
| layout          | 分页布局               | String   | 'total, sizes, prev, pager, next, jumper' |
| total           | 数据总数               | Number   | 0                                         |
| data            | 数据                   | Array    |                                           |
| columns         | 列头                   | Array    |                                           |
| pagination      | 是否分页               | Boolean  | false                                     |
| localPagination | 是否启用本地分页       | Boolean  | false                                     |
| mergeProps      | 需要合并的列属性名数组 | String[] | []                                        |
|                 |                        |          |                                           |
|                 |                        |          |                                           |

下面给是使用实例

```html
<template>
  <data-table
    v-model:page-size="pageSize"
    v-model:current-page="currentPage"
    :data="tableData"
    :columns="column"
    :total="total"
    :pagination="true"
    local-pagination
    :border="true"
    :merge-props="['name', 'age']"
  />
</template>

<script setup>
  const column = [
    { prop: 'name', label: '姓名' },
    { prop: 'age', label: '年龄' },
    { prop: 'address', label: '地址' }
  ]
  const tableData = [
    { name: '张三', age: 20, address: '北京' },
    { name: '张三', age: 20, address: '上海' },
    { name: '李四', age: 25, address: '广州' },
    { name: '李四', age: 25, address: '深圳' },
    { name: '王五', age: 30, address: '杭州' }
  ]
  // 分页相关
  const currentPage = ref(1)
  const pageSize = ref(10)
  const total = ref(100)
</script>
```
