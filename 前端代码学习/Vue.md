# Vue





```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="../vue1026.js"></script>
    <style>
        #tb{
            width: 800px;
            margin: 20px auto;
            border-collapse: collapse;
        }
        #tb th{
            border: 1px solid black;
            color: white;
            background-color: blue;
        }
        #tb td{
            text-align: center;
            border: 1px solid black;
        }
    </style>
</head>
<body>
    <div id="app">
        <input type="text" v-model="pid">
        <input type="text" v-model="pname">
        <button @click="addData">添加数据</button>

        <table id="tb">
            <tr>
                <th>编号</th>
                <th>品牌</th>
                <th>创建时间</th>
                <th>操作</th>
            </tr>
            <tr v-show="list.length == 0">
                <td colspan="4">暂无数据</td>
            </tr>
            <tr v-for="item in list">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.ctime | filter 'yyyy-mm-dd'}}</td>
                <td>
                    <a href="javascript:void(0)" @click="deleteData(item.id)">删除</a>
                </td>
            </tr>
        </table>
    </div>
</body>
<script>
    Vue.filter('filter',function(input,fmtString){
        var year = input.getFullYear()
        var month = input.getMonth() + 1;
        var day = input.getDate();

        var res = year + '-' + month + '-' + day;

        if(fmtString == 'yyyy-mm-dd'){
            return res
        }
    })

    var vm = new Vue({
        el:'#app',
        data:{
            list:[
                {id:01,name:'奔驰',ctime:new Date()}
            ],
            pid:0,
            pname:''
        },
        methods:{
            addData:function(){
                // 添加数据
                var obj = {id:this.pid,name:this.pname,ctime:new Date()}

                // 把添加的对象,添加到数组中去
                this.list.push(obj)

                // 清空
                this.pid = 0
                this.pname = ''
            },
            deleteData:function(id){

                if(!confirm('你真的要删吗?')){
                    return;
                }

                // 删除数据
                var index = this.list.findIndex(function(item){
                    return item.id == id
                })

                // 从数组中删除对应的数据
                this.list.splice(index,1)
            }
        }
    })
</script>
</html>
```

