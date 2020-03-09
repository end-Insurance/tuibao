<template>
  <div class="header">
      <div class="logo">
          <img src="@/assets/logo.png" alt="">
      </div>
      <div class="inner_list">
          <ul>
              <li v-for="(item,index) in inner_list" :key="index">{{item}}</li>
          </ul>
          <button class="login_btn">登录</button>
      </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
        inner_list:[
            '流程介绍',
            '业务范围',
            '成功案例',
            '关于我们'
            ]
        }
    }

}
</script>

<style lang="scss" scoped>
    .header {
        background: #fff;
        display: flex;
        justify-content: space-between;
        height: 115px;
        width: 100%;
        .inner_list {
               display: flex;
                //  justify-items: center;
                    align-items: center;
            ul {
                margin: 0;
             
                li {
                    cursor: pointer;
                    display: inline-block;
                    padding-left: 20px;
                    font-size: 22px;
                    list-style: none;
                    &:hover {
                        color:crimson
                    }
                }
            }
            .login_btn {
                margin: 0 50px;
                width: 100px;
                height: 40px;
                line-height: 30px;
                border: none;
                font-size: 20px;
                &:hover {
                    background: darkgrey;
                }
            }
        }
        
    }
</style>
