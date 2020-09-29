<template>
  <div class="content">
    <Calendar
      ref="Calendar"
      :markDate="markDate"
      :markDateMore="markDateMore"
      agoDayHide="1601481600"
      futureDayHide="1604073600"
      @choseDay="clickDay"
      @changeMonth="changeDate"
      @isToday="isToday"
      :canChoose="false"
    ></Calendar>
    <br>
    <h3>markDateMore：标记多种颜色，1号2号一种风格,3号四号另一种风格</h3>
    <br>
    <h3>markDate：单一标记，多个日期同一种标记，23号，24号</h3>
    <div class="bt-box">
      <div class="bt-jump" @click="() => $refs.Calendar.ChoseMonth('2018-12-12')">跳转至 2018-12-12 并选中</div>
      <div class="bt-jump" @click="() => $refs.Calendar.ChoseMonth('2018-12-12',false)">跳转至 2018-12-12 不选中</div>
    </div>
  </div>
</template>

<script>
import 'vue-mark-calendar/lib/vue-mark-calendar.css'
// import Calendar from 'vue-mark-calendar'
import Calendar from '../../packages/index.js'
export default {
  data() {
    return {
      markDate: ['2019-04-23','2019-04-24'],
      markDateMore: [
        {
          date: "2019-04-01",
          className: "mark1"
        },
        {
          date: "2019-04-02",
          className: "mark1"
        },
        {
          date: "2019-04-03",
          className: "mark2"
        },
        {
          date: "2019-04-04",
          className: "mark2"
        },
      ]
    };
  },
  components: {
    Calendar
  },
  methods: {
    isToday(val){
      console.log(`isToday：${val}`)
    },
    clickDay(data) {
      console.log("选中了", data); //选中某天
    },
    clickToday(data) {
      console.log("跳到了本月今天", data); //跳到了本月
    },
    changeDate(data) {
      console.log("左右点击切换月份", data); //左右点击切换月份
    },
    demo() {
      this.$refs.Calendar.ChoseMonth("2018-12-12"); //跳到12月12日选中12月12日
    }
  },
}
</script>

<!-- Add "scoped " attribute to limit CSS to this component only -->
<style scoped>
h3 {
  text-align: center;
  width: 90%;
  margin: auto;
  color: darkgrey;
}

.bt-box{
  width: 200px;
  margin: 0 auto;
}

.bt-jump {
  margin: auto;
  padding: 10px 15px;
  display: inline-block;
  background: #0fc37c;
  border-radius: 4px;
  color: #fff;
  font-size: 13px;
  text-align: center;
  margin-top: 20px;
}
.bt-jump:hover{
  opacity: 0.8;
  cursor: pointer;
}

.wh_container >>> .mark1 .wh_item_date_text{
  background-color: #0fc37c;
  color: #fff;
}

.wh_container >>> .mark2 .wh_item_date_text{
  background-color: #ad4a95;
  color: #fff;
}
</style>