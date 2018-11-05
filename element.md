### element 
#### datetilepicker 设置默认时间范围

##### 单个输入框的

组件代码：
```
<el-date-picker
       v-model="value1"
       type="date"
       placeholder="选择日期"
       :picker-options="pickerOptions0">
</el-date-picker>
```
情景1: 设置选择今天以及今天之后的日期
```
data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() < Date.now() - 8.64e7;
          }
        },  
   }     
}  
```
情景2: 设置选择今天以及今天以前的日期
```
 data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() > Date.now() - 8.64e6
          }
        },  
   }     
} 
```  
情景3: 设置选择今天之后的日期（不能选择当天时间）
```
 data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() < Date.now();
          }
        },  
   }     
}
```
情景4: 设置选择今天之前的日期（不能选择当天）
```
 data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            return time.getTime() > Date.now();
          }
        },  
   }     
}
```
情景5: 设置选择三个月之前到今天的日期
```
 data (){
   return {
       pickerOptions0: {
          disabledDate(time) {
            let curDate = (new Date()).getTime();
            let three = 90 * 24 * 3600 * 1000;
            let threeMonths = curDate - three;
            return time.getTime() > Date.now() || time.getTime() < threeMonths;;
          }
        },  
   }     
} 
```
两个输入框

组件代码
```
 <el-date-picker
       v-model="value1"
       type="date"
       placeholder="开始日期"
       :picker-options="pickerOptions0">
</el-date-picker>
<el-date-picker
       v-model="value2"
       type="date"
       placeholder="结束日期"
       :picker-options="pickerOptions1">
</el-date-picker>
```
情景1: 限制结束日期不能大于开始日期
```
 data(){
    return {
         pickerOptions0: {
                disabledDate: (time) => {
                    if (this.value2 != "") {
                        return time.getTime() > Date.now() || time.getTime() > this.value2;
                    } else {
                        return time.getTime() > Date.now();
                    }
            }
        },
        pickerOptions1: {
            disabledDate: (time) </span>=&gt;<span style="color: #000000;"> {
                </span><span style="color: #0000ff;">return</span> time.getTime() &lt; <span style="color: #0000ff;">this</span>.value1 || time.getTime() &gt;<span style="color: #000000;"> Date.now();
            }
        },
} 
```

