<template>
    <div class="movie_wrapper">
        <div class="movie">
            <div class="movie_img_wrapper">
                <img :src="movies.Poster" alt=" " class="movie_img">
            </div>
            <p>Name: {{movies.Title}}</p>
            <p>Year: {{movies.Year}}</p>
            <p>imdbID: {{movies.imdbID}}</p>
            <p>Type: {{movies.Type}}</p>
        </div>
    </div>  
</template>

<script>
    export default {
        props: ['movies']
    }
</script>
    
<style>
    .movie_wrapper{
        margin: 2% 1%;
    }
    .movie_img_wrapper {
        width: 80%;
        box-shadow: 0px 0px 27px 2px #223c5099;
    }
    .movie_img{
        width: 100%;
        margin-top: 2%;
    }
</style>