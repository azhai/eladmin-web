<!--日期选择-->
<template>
  <el-date-picker
    :picker-options="{ shortcuts: calendarShortcuts }"
    :value-format="valueFormat"
    :default-time="['00:00:00','23:59:59']"
    type="daterange"
    range-separator=":"
    size="small"
    class="date-item"
    start-placeholder="开始日期"
    end-placeholder="结束日期"
  />
</template>

<script>
import { calendarShortcuts } from '@/utils/shortcuts'
export default {
  name: 'DateRangePicker',
  props: {
    valueFormat: {
      type: String,
      default: 'yyyy-MM-dd HH:mm:ss'
    }
  },
  computed: {
    calendarShortcuts: {
      get() { return calendarShortcuts }
    }
  }
}
</script>
