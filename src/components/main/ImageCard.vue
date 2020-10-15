<template>
  <div class="image-card">
    <div class="image-wrapper" @mouseover="mouseover" @mouseleave="mouseleave">
      <!-- hover효과 @mouseover="mouseover" @mouseleave="mouseleave" / script methods에 mouseover+mouseleave해주기  -->
      <img :src="url" alt="">
      <transition name="fade">
        <div class="cover" v-if="isShow" >
            <v-text-field
              v-bind="attrs"
              v-on="on"
              v-model="author"
              solo
              append-icon="mdi-chevron-down"
              label="Regular"
              class="menu"
              @click="menuClick"
            >
            </v-text-field>
            <div class="right-btn" @click="menuClick">저장</div>
            <v-card width="200" class="list-card" v-if="isMenuShow">
              <v-list>
                <v-list-item
                v-for="(item, index) in items"
                :key="index"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-card> 
        <div class="under-wrapper">
          <v-btn icon dark><v-icon>mdi-upload</v-icon></v-btn>
          <v-btn icon dark><v-icon>mdi-dots-horizontal</v-icon></v-btn>
        </div>
        </div>
      </transition>
    </div> 
      <p>{{author}}</p>
  </div>
</template>

<script>
  export default {
    name: 'ImageCard',
    data() {
      return {
        isMenuShow: false,
        isShow: false,
        category:'cloth',
        items:[
          {title:'Click Me'},
          {title:'Click Me'},
          {title:'Click Me'},
          {title:'Click Me 2'}
        ]
      }
    },
    props: ['url', 'author'],
    methods:{
      mouseover(){
        this.isShow = true
      },
      mouseleave(){
        this.isShow = false
      },
      menuClick() {
        this.isMenuShow = !this.isMenuShow
      },
    },
  }
</script>

<style lang="scss" scoped>
.image-wrapper {
  position:relative;
}
.cover {
  background-color:rgba(#222,0.3);
  // 위에께 축약본= background-color:rgba($color:#222,$alpha:0.3);
  position: absolute;
  top:0;
  bottom:7px;
  left:0;
  right:0;
  border-radius: 10px;

}
.menu{
  width:60%;
  margin:20px;
  border-radius: 10px 0 0 10px;
}
.right-btn {
  background:rgba(230,0,35,.9);
  display:inline-block;
  width:20%;
  height:48px;
  border-radius: 0px 10px 10px 0;
  position: absolute;
  right:40px;
  top:20px;
  color:#fff;
  text-align:center;
  line-height: 3.2;
}

.under-wrapper{
  position: absolute;
  right:10px;
  bottom:10px;
}
.list-card {
  top:-50px;
  left:10px;
  z-index: 1;
}
.image-card img {
  border-radius: 10px;
}
p{
  font-weight: bold;
}

// animation
.fade-enter-active, .fade-leave-active{
  transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

</style>