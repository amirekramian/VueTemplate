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
  padding: 5px;
  margin: 15px;
  background: #18008513;
  width: 190px;
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
</style>