<template>
  <div class="date-wrapper">
    <div class="week">
      <span>一</span>
      <span>二</span>
      <span>三</span>
      <span>四</span>
      <span>五</span>
      <span>六</span>
      <span>日</span>
    </div>
    <div class="date-list">
      <span v-for="i in spaceCount" :key="'s' + i"></span>
      <span
        v-for="i in monthCount"
        :key="'m' + i"
        :class="{'date-now': currentDay === i}"
      >
        {{i}}
      </span>
    </div>
    <div class="time-box">
      <span>{{time.h}}</span>
      <span class="point">:</span>
      <span>{{time.m}}</span>
      <span class="point">:</span>
      <span>{{time.s}}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Date',
    data () {
      return {
        currentDate: new Date(),
        monthCount: 0,
        spaceCount: 0,
        currentDay: 0,
        time: {
          h: '00',
          m: '00',
          s: '00'
        }
      }
    },
    watch: {
      currentDate () {
        this.changeTime()
      }
    },
    created () {
      setInterval(() => {
        this.currentDate = new Date()
      }, 1000)
      this.changeTime()
    },
    methods: {
      changeTime () {
        let year = this.currentDate.getFullYear(),
          month = this.currentDate.getMonth(),
          date = this.currentDate.getDate(),
          h = this.currentDate.getHours().toString(),
          m = this.currentDate.getMinutes().toString(),
          s = this.currentDate.getSeconds().toString()
        this.spaceCount = new Date(year, month, 1).getDay() - 1
        this.monthCount = new Date(year, month + 1, 0).getDate()

        this.currentDay = date
        this.time = {
          h: h.length === 2 ? h : '0' + h,
          m: m.length === 2 ? m : '0' + m,
          s: s.length === 2 ? s : '0' + s
        }
      }
    }
  }
</script>

<style scoped lang="less">
  .week {
    display: flex;
    width: 100%;
    border-bottom: 1px solid #eee;
    & > span {
      flex: 1;
      text-align: center;
      font-size: 20px;
      line-height: 50px;
    }
  }

  .date-list {
    font-size: 0;
    height: 300px;
    span {
      display: inline-block;
      width: 14.24%;
      font-size: 24px;
      height: 50px;
      line-height: 50px;
      text-align: center;
      vertical-align: middle;
      &.date-now {
        background: orange;
        border-radius: 50%;
        color: #fff;
      }
    }
  }

  .time-box {
    text-align: center;
    font-size: 40px;
    margin-top: 10px;
    border-top: 1px solid #eee;
    border-bottom: 1px solid #eee;
    line-height: 65px;
    vertical-align: middle;
    font-weight: 500;
  }
</style>
