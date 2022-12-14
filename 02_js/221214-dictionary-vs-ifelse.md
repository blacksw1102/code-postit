# dictionary vs if else

condition이 2~3개 정도면 ifelse 방식을, 그 이상일 경우에는 dictionary 방식을 권장한다.

## dictionary 방식

```js
const dayDict = {
  monday: 1,
  tuesday: 2,
  wednesday: 3,
  thursday: 4,
  friday: 5,
  saturday: 6,
  sunday: 7,
}

function getDayNumber(day) {
  return dayDict[day]
}
```

## ifelse 방식

```js
function getDayNumber(day) {
  if (day === 'monday') return 1
  if (day === 'tuesday') return 2
  if (day === 'wednesday') return 3
  if (day === 'thursday') return 4
  if (day === 'friday') return 5
  if (day === 'saturday') return 6
  if (day === 'sunday') return 7
}
```
