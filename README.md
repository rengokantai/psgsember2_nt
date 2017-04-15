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
