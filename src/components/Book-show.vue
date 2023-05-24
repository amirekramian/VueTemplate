<template>
  <div class="mainbody" id="app">
    <br />
    <div>
      <button class="btn btn-default" @click="FavoriteOnlyToggle()">
        <span v-if="!favoriteOnly">Show only favorite books</span>
        <span v-if="favoriteOnly">Show all books</span>
      </button>
    </div>
    <ul class="flex" v-if="!favoriteOnly">
      <li v-for="item in Books" :key="item.id" @dblclick="LikeBook(item)">
        <div class="picbox" :class="{ fav: item.isfav , save:item.issaved , favsave:item.isfav && item.issaved}">
          <div>
            <img :src="item.imgsrc" class="bookPic" />
            <div>
              <b>{{ item.title }}</b>
              <br />
              <p>author: {{ item.author }}</p>
              <p>Release year: {{ item.releaseyear }}</p>
              <div class="buttonflex">
              <button class="btn " @click="LikeBook(item)">
                <img class="icon" src="@/assets/Icons/Liked.svg" v-if="item.isfav" alt="">
                <img class="icon" src="@/assets/Icons/Like.svg" v-if="!item.isfav" alt="">
              </button>
              <button class="btn" @click="SaveBook(item)" >
                <img class="icon" src="@/assets/Icons/Saved.svg" v-if="item.issaved" alt="">
                <img class="icon" src="@/assets/Icons/Save.svg" v-if="!item.issaved" alt="">

              </button>
              <button class="btn" @click="ShareBook(item)" >
                <img class="icon" src="@/assets/Icons/Comment.svg"  alt="">
              </button>
              </div>
              <button class="btn">more detail</button>
              <br />
            </div>
          </div>
        </div>
      </li>
    </ul>
    <ul class="flex" v-if="favoriteOnly">
      <li v-for="item in Books" :key="item.id" @dblclick="LikeBook(item)">
        <div class="picbox" :class="{ fav: item.isfav }">
          <div>
            <img :src="item.imgsrc" class="bookPic" />
            <div>
              <b>{{ item.title }}</b>
              <br />
              <p>author: {{ item.author }}</p>
              <p>Release year: {{ item.releaseyear }}</p>
              <button class="btn btn-success" @click="LikeBook(item)">
                <span v-if="!item.isfav">Like this book</span>
                <span v-if="item.isfav">You liked this book</span>
              </button>
              
              <br />
            </div>
          </div>
        </div>
      </li>
    </ul>
    <br />

    <!-- <div class="box" @mouseover="EventHandler($event,'over')">mouse Over</div>
    <div class="box" @mouseleave="EventHandler($event,'leave')">Mouse Leave</div>
    <br>
    <div class="box" @dblclick="EventHandler($event,'double')">double click</div>
    <div class="box" @click="EventHandler($event,'click')">Mouse Click</div>
    <br>
    <div class="box" @mousemove="HandleMouseMove">{{x}}-{{y}}</div> -->
  </div>
</template>

<script>
export default {
  props: ["BookData", "favoriteOnly"],
  data() {
    return {
      Books: this.BookData,
      FavoritOnly: this.favoriteOnly,
    };
  },
  methods: {
    LikeBook(item) {
      this.Books[item.id].isfav = !this.Books[item.id].isfav;
    },
    FavoriteOnlyToggle() {
      this.FavoritOnly = !this.FavoritOnly;
      console.log(this.FavoritOnly);
    },
    SaveBook(item){
        this.Books[item.id].issaved=!this.Books[item.id].issaved;
    }
  },
  computed:{
    ReturnfavoriteBooks(){
            return this.Books.filter((book)=> book.isfav)
        }
  }
};
</script>


<style scoped>
.box {
  padding: 100px 0;
  width: 400px;
  text-align: center;
  background: #92bdff;
  margin: 20px;
}

.bookPic {
  max-width: 150px;
  max-height: 200px;
}

.picbox {
  border-radius: 15px;
  padding: 10px;
  margin: 15px;
  background: #18008513;
  width: 250px;
  align-items: center;
  text-align: center;
}

div.fav {
  border-radius: 15px;
  background: #ffc8c8;
  width: 190px;
  align-items: center;
  text-align: center;
}

.flex {
  justify-content: center;
  align-items: center;
  display: flex;
  flex-wrap: wrap;
}

ul {
  list-style: none;
}

button.faved {
  border-color: #00c431;
  background-color: white;
  color: black;
}
.mainbody {
  width: 90%;
  margin: auto;
}
.buttonflex{
    width: 100%;
  justify-content: center;
  align-items: center;
  display: flex;
}
.icon{
    width: 25px;
}

div.save{
  border-radius: 15px;
  background: #c8ffda;
  width: 190px;
  align-items: center;
  text-align: center;
}

div.favsave{
  border-radius: 15px;
  background: #ffbb006b;
  width: 190px;
  align-items: center;
  text-align: center;
}
</style>