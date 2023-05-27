<template>
  <Header>
  <template v-slot:HeaderMore>
<h1>Hellooooo</h1>
<br>
<h2>Welcome to your book shop</h2>
  </template>
  <p>this is a Default slot. default slots does not need to template tag</p> 
  </Header>

  <BooksShow :BookData="books" :favoriteOnly="favoriteOnly" :FavBooks="favoriteBooksData" :saveOnly="saveOnly" :saveBooks="savedBookData" @FavsClick="ReturnFavoriteBooks" @SavedClick="ReturnSavedBooks" />
  <!-- <Modal /> -->
  <Footer />
</template>

<script>
// import Modal from './components/Modal-v'
import BooksShow from './components/Book-show'
import Header from './components/Header-Part'
import Footer from './components/Footer-part'




export default {
  name: 'App', 
  components:{
    // Modal,
    BooksShow,
    Header,
    Footer
  },
  data(){
    return{
      favoriteBooksData:"",
      savedBookData:"",
      visibility: true,
             books :[
                 {id:0,title:'Pride and Prejudice', releaseyear: 1813 , author:'jane austin' , imgsrc:require('@/assets/Images/BeachRead.jpg'), isfav : false,issaved:false},
                 {id:1,title:'Seven Days in june', releaseyear: 2021 , author:'andre aciman', imgsrc: require('@/assets/Images/PrideandPrejudice.jpg'), isfav : false,issaved:false},
                 {id:2,title:'Beach Read', releaseyear: 2020 , author:'Emily Henry',imgsrc: require('@/assets/Images/SevenDaysInJune.jpg'), isfav : false,issaved:false},
                 {id:3,title:'The Notebook', releaseyear: 1996 , author:'Nicholas Sparks',imgsrc: require('@/assets/Images/TheNotebook.jpg'), isfav : false,issaved:false},
                 {id:4,title:'Me Before You', releaseyear: 2012 , author:'Nicholas Sparks',imgsrc: require('@/assets/Images/MeBeforeYou.jpg'), isfav : false,issaved:false},
                 {id:5,title:'Outlander', releaseyear: 1991 , author:'diana gabaldon',imgsrc: require('@/assets/Images/Outlander.jpg'), isfav : false,issaved:false},
                 {id:6,title:'The Flatshare', releaseyear: 2019 , author:'beth oleary',imgsrc: require('@/assets/Images/TheFlatshare.jpg'), isfav : false,issaved:false},
                 {id:7,title:'One Last stop', releaseyear: 2021 , author:'casey Mcquiston',imgsrc: require('@/assets/Images/thelaststop.jpg'), isfav : false,issaved:false},
                 {id:8,title:'Love on the brain', releaseyear: 2019 , author:'Beth oleary',imgsrc: require('@/assets/Images/TheNotebook.jpg'), isfav : false,issaved:false},
                 {id:9,title:'The Fault in Our Stars', releaseyear: 2012 , author:'john green',imgsrc: require('@/assets/Images/TheFaultinOurStars.jpg'), isfav : false,issaved:false}
                    ],
             favoriteOnly: false,
             saveOnly: false
             //favoriteBooksData: ReturnFavoriteBooks()
    }
  },
  methods:{
    ReturnFavoriteBooks(){
      this.favoriteBooksData=this.books.filter((book) => book.isfav)
    },
    ReturnSavedBooks(){
    this.savedBookData = this.books.filter((book) => book.issaved)
    console.log("appvue",this.savedBookData)
    }
    
  },
  computed:{

  }
  }
  
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
