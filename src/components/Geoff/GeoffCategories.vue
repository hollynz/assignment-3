<template>
    <div class="categories-container">
        <div class="category festivals">
            <div class="title">

            </div>
        </div>
        <div class="category music-venues">
            <div class="title">

            </div>
        </div>
        <div class="category record-stores">
            <div class="title">

            </div>
        </div>
        <div class="category music-shops">
            <div class="title">

            </div>
        </div>
        <div class="category music-schools">
            <div class="title">

            </div>
        </div>


    </div>
    
</template>

<script>
export default {
  name: "GeoffCategories",
  components: {}
};
</script>

<style>
.categories-container {
  display: flex;
  flex-flow: row nowrap;
  justify-content: center;
  align-items: center;
}
.festivals {
    background-image: url(../../assets/geoff/category-festivals.jpg);
    filter: grayscale(100%);
    transition: all 0.5s linear;
}

.festivals:hover {
    transition: all 0.5s linear;
    filter: grayscale(0%);
}

.music-venues {
    background-image: url(../../assets/geoff/category-music-venues.jpg);
    filter: grayscale(100%);
    transition: all 0.5s linear;
}

.music-venues:hover {
    transition: all 0.5s linear;
    filter: grayscale(0%);
}

.record-stores {
    background-image: url(../../assets/geoff/category-record.jpg);
    filter: grayscale(100%);
    transition: all 0.5s linear;
}

.record-stores:hover {
    transition: all 0.5s linear;
    filter: grayscale(0%);
}

.music-shops {
    background-image: url(../../assets/geoff/category-music-shop.jpg);
    filter: grayscale(100%);
    transition: all 0.5s linear;
}

.music-shops:hover {
    transition: all 0.5s linear;
    filter: grayscale(0%);
}

.music-schools {
    background-image: url(../../assets/geoff/category-music-schools.jpg);
    filter: grayscale(100%);
    transition: all 0.5s linear;
}

.music-schools:hover {
    transition: all 0.5s linear;
    filter: grayscale(0%);
}

.category {
    display: grid;
    margin: auto;
    position: relative;
    flex: 1;
    text-align: center;
    color: white;
    transition: .3s;
    max-width: 20%;
    height: 100vh;
    min-width: 10%;
    background-color: rgba(#222, .4);
}

.category::before {
    display: grid;
    margin: auto;
    position: relative;
    flex: 1;
    text-align: center;
    color: white;
    transition: .3s;
    max-width: 20%;
    height: 100vh;
    min-width: 10%;
}

.category:hover {
    transition: .5s;
    max-width: 40% !important;
    flex-grow: 2;
    cursor: pointer;
    color: #fff;
}

.title{
    margin: auto;
    font-size: 2em;
}
</style>
