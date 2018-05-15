# vue.js-components
vue.js--子组件触发子组件方法，父组件触发自己方法并改变子组件事件


                  <div id="app">
                    <button @click="fun">点击</button>
                    <chin></chin>
                  </div>

                   var vm=new Vue({
                       el:"#app",
                       methods:{
                        fun:function(){
                         this.$children[0].abc=true;
                        }
                       },
                      components:{
                      chin:{
                        template:'<div v-if="abc" @click="show_text">我是子组件</div>',
                          data:function(){
                                  data:{
                                  return{
                                    abc:false
                                  }
                              }
                            },
                          methods:{
                            show_text:function(){
                              this.abc=!this.abc;
                            }
                          }
                        }
                       }
                    })



    
    全局组件 与 局部组件
    
        <div id="app">
         <linas :loo="text">局部组件</linas>
         <rtt  :mes="text">全局组件</rtt>
         <div>{{text|id_name}}</div>
         <div>{{getnum}}</div>
       </div>
    
    
      	//过滤函数
          Vue.filter("id_name",function(val){
            return val.split("").reverse().join("")
          })
          
        //全局组件传值
         Vue.component("rtt",{
            template:"<div>全局组 ' {{mes}}  '建</div>",
             props:{
              mes:{
                type:String
              }
            }
         })

            var app = new Vue({  
                  el : '#app',  
                  data:{
                    text:'林雨轩大帅哥87878787'
                  },
                  //局部组件传值
                  components : {  
                       'linas': {  
                           template:'<div>我是局部的" {{loo}} "一个组件</div>' ,
                           props:["loo"]
                     }  
            } ,
            //计算属性  相当于vue 1.0 的过滤函数
            computed:{
              getnum:function(){
                return this.text.split("").reverse().join("")  		
              }
        //  	 val.split("").reverse().join("")
            }
        })  
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
