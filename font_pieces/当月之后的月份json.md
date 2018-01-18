#获取当月以及当月之后的月份json

```
let nowDateYear = Number(dateTransNum(new Date()).toString().substr(0, 4));
let nowDateMonth = Number(dateTransNum(new Date()).toString().substr(4, 2));
this.addYearMode = {
    '0': nowDateYear,
    '1': nowDateYear + 1,
    '2': nowDateYear + 2,
    '3': nowDateYear + 3,
    '4': nowDateYear + 4,
    '5': nowDateYear + 5,
    '6': nowDateYear + 6,
    '7': nowDateYear + 7,
    '8': nowDateYear + 8,
    '9': nowDateYear + 9,
    '10': nowDateYear + 10,
    '11': nowDateYear + 11
};
this.addMonthMode = {};
let index = 0;
for (let i = nowDateMonth; i <= 12; i++) {
    let showMonth = nowDateMonth + index;
    index++;
    if (showMonth < 10) {
        showMonth = '0' + showMonth.toString();
    } else {
        showMonth = showMonth.toString();
    }
    this.addMonthMode[index + ''] = showMonth;
}
```