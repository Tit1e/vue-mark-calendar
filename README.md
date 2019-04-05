# vue-mark-calendar

## 🏆 fork from [vue-calendar](https://github.com/zwhGithub/vue-calendar)
修改自 [vue-calendar](https://github.com/zwhGithub/vue-calendar)，非常感谢作者🙏提供这么好用的插件。

## 修改原因
公司项目开发过程中需要用到不同日期的标记，发现了 [vue-calendar](https://github.com/zwhGithub/vue-calendar)，但是由于公司使用的是 element-ui ，因此配色上有较大的出入，这是修改的主要原因。
还有一个原因是公司项目中用到的日期格式都是 '2019-04-01'，而插件中使用的格式是 '2019/04/01'，使用过程中会出现一层转换，并且插件返回的值月份日期小于 9 时不会添 0，还有一些另外的定制化需求，因此做了一些调整。

[在线 Demo](https://evolly.one/demos/vue-mark-calender/index.html)

![](https://personal-1251959693.cos.ap-chengdu.myqcloud.com/2019-04-05-084559.png)

## Install

```javascript
npm i vue-mark-calendar --save
yarn add vue-mark-calendar
```

## Usage
```html
// 基本用法
<Calendar
  ref="Calendar"
  :markDate="markDate"
  :markDateMore="markDateMore"
  >
</Calendar>
```
```css
//css,element-ui的选中效果有两层背景颜色，因此我在原来结构上加了一层标签，并加上了 class：wh_item_date_text，
如果需要 element-ui 的选中样式，则背景颜色需要加在 wh_item_date_text 上，否则可以不加 wh_item_date_text
具体效果可自行尝试。

.wh_container >>> .mark1 .wh_item_date_text{
  background-color: #0fc37c;
  color: #fff;
}

.wh_container >>> .mark2 .wh_item_date_text{
  background-color: #ad4a95;
  color: #fff;
}
```
```javascript
//vue文件中引入
import Calendar from 'vue-mark-calendar';
export default {
  components: {
    Calendar
  },
  data(){
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
    }
  }
}
// 使用 Methods
this.$refs.Calendar.changeMonth('2018-01-01') //跳转后选中 2018-01-01
this.$refs.Calendar.changeMonth('2018-01-01', false) //跳转后不选中 2018-01-01
```
如仍有疑问可看 [Demo](./src/views/demo.vue)。

## Attributes

| 参数 | 说明 | 类型 | 可选值 | 默认值 |
| ------ | ------ | ------ | ------ | ------ |
| markDate | 单一标注，传入日期数组["2018/2/2","2018/2/6"] | Array | - | [] |
| markDateMore | 多种标记，使用方法见 Usage | Array | - | [] |
| agoDayHide | 某个日期以前的不允许点击 时间戳长度是 10 位 | String | - | 0 |
| futureDayHide | 某个日期以后的不允许点击 时间戳长度是 10 位 | String | - | 2554387200 |
| sundayStart | 默认是周一开始 当是true的时候 是周日开始 | Boolean | true/false | false |
| textTop | 日历头部的文字 | Array | - | [ '日','一', '二', '三', '四', '五', '六'] |
| borderRadius | 整个日历块的圆角 | String | - | 4px |
| showToday | 在日历中高亮今天的日期 | Boolean | true/false | true |
| canChoose | 日历中日期能否选择 | Boolean | true/false | true |

## Events
| 事件名称 | 说明 | 回调参数 |
| ------ | ------ | ------ |
| choseDay | 选中某天的回调  | YY-MM-DD |
| changeMonth | 切换月份的回调 | YY-MM-DD |
| isToday | 切换月份的时候，只有切到当月才会调用这个方法，返回今天的日期 | YY-MM-DD |
## Methods
| 事件名称 | 说明 | 参数 |
| ------ | ------ | ------ |
| changeMonth | 切换月份，日期格式：YYYY-MM-DD，isChoose默认为 true,跳转后自动选中跳转日期 | (date,isChoose) |
| PreMonth | 跳转到上月 | - |
| NextMonth | 跳转到上月 | - |