# hc-coin-eval-calc

> A Vue.js project

## Basic Use

```html
<div id="app"></div>

<script src="https://commbocc.github.io/hc-coin-eval-calc/dist/build.js"></script>
<script>
new HcCoinEvalCalc().$mount('#app')
// // the above is the same as:
// new HcCoinEvalCalc({ propsData: {
//   title: 'Employee Probation/Evaluation Dates',
//   midTermVal: 3,
//   midTermUnit: 'months',
//   endTermVal: 6,
//   endTermUnit: 'months'
// }}).$mount('#app')
</script>
```

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
