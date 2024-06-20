<template>
  <view class="index">
    <input placeholder="可正常输入"/>
    <input :disabled="false" placeholder="被禁用"/>
    <input :disabled="true" placeholder="被禁用"/>
    <view>{{year}}年{{month}}月{{day}}日</view>
    <picker-view indicator-style="height: 30px;" style="width: 100%; height: 300px;" :value="value" @change="onChange">
      <picker-view-column>
        <view v-for="(item, index) in years" :key="index">{{item}}年</view>
      </picker-view-column>
      <picker-view-column>
        <view v-for="(item, index) in months" :key="index">{{item}}月</view>
      </picker-view-column>
      <picker-view-column>
        <view v-for="(item, index) in days" :key="index">{{item}}日</view>
      </picker-view-column>
    </picker-view>
  </view>
</template>

<script>
  export default {
    name: "Index",
    data() {
      const date = new Date()
      const years = []
      const months = []
      const days = []
      for (let i = 1990; i <= date.getFullYear(); i++) {
        years.push(i)
      }
      for (let i = 1; i <= 12; i++) {
        months.push(i)
      }
      for (let i = 1; i <= 31; i++) {
        days.push(i)
      }
      return {
        years: years,
        year: date.getFullYear(),
        months: months,
        month: 2,
        days: days,
        day: 2,
        value: [3, 1, 1]
      }
    },

    methods: {
      onChange: function(e) {
        const val = e.detail.value
        console.log(val)
        this.year = this.years[val[0]]
        this.month = this.months[val[1]]
        this.day = this.days[val[2]]
      }
    }
  }
</script>