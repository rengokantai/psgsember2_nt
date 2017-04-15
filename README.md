# psgsember2_nt
## 10.Triggering Events and Actions
### 4 Sending Actions
#### 04:13
Action Bubbling
- Production Controller-> Production route handler->Application Route Handler  


To avoid this we should use a component

#### 05:54 Data Down Actions Up (DDAU)
the transition method should happen in route. ( routes/production.js)
```
actions:{
  loadData(url){
    this.transitionTo(url);
  }
}
```
in production component(production.hbs)
```
{{loopy-loader action="loadData"}}
```
in action:(xomponents/loppy-loader.js)
```
actions:{
  loadData(){
    let newStart = this.get('start_time');
    let url = `/${newStart}/to/${newEnd}`;
    this.sendAction("action",url);
    }
}
```
#### 06:49 use closure
A closure is when a function is packaged with its vairable has access to.

#### 08:03
```
ember install ember-route-action-helper
```
And
in production component(production.hbs),change
```
{{loopy-loader action="loadData"}}
```
to
```
load = (route-action 'loadData')
```

#### 08:32
in loopy-loader.js,change
```
loadData(){
    let newStart = this.get('start_time');
    let url = `/${newStart}/to/${newEnd}`;
    this.sendAction("action",url);
    }
```
to
```
this.get('load')(url)
```

### 5 More closure Actions
table-production
```
actions:{
  sortData(sortBy){ sort data here}
}
```
and table-th
```
actions:{
sort(){ this.get('sortData')(sortBy);
}
```
