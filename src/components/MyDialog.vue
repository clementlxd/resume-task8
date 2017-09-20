<template>
  <div class="dialogWrapper" v-show="visible">
    <div class="dialog">
      <header>
        {{title}}
        <span class="close" @click="close">X</span>
      </header>
      <main>
        <slot></slot>
      </main>
    </div>
  </div>
</template>

<script>
  export default{
    name:'MyDialog',
    props:['title','visible'],
    methods:{
      close(){
        this.$emit('close')
      }
    }
  }
</script>


<style scoped lang="scss">
  .dialogWrapper{
    position:fixed;
    background: silver;
    border:1px solid grey;
    border-radius:4px;
    top:50%;
    left:50%;
    //bottom:0;
    //right:0;
    //margin:0;
    //display: flex;
    //justify-content:center;
    transform:translate(-50%,-50%);
    height:200px;
    width:300px;


  }
  .dialog{
    background: white;
    min-height:4em;
    min-width:10em;
    >header{
      padding: 16px;
      display: flex;
      justify-content:space-between;
      .close{
        cursor:pointer;
      }
    }
    >main{
      padding: 16px;
    }

  }
</style>




























