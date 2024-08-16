<script setup>

</script>

<template>

    <div class="gallery">

        <div class="gallery-item"> 
            <img src="@/assets/pessoa1.jpg" alt="">
            <div class="overlay"> Image 1 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa2.jpg" alt="">
            <div class="overlay"> Image 2 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa3.jpg" alt="">
            <div class="overlay"> Image 3 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa4.jpg" alt="">
            <div class="overlay"> Image 4 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa5.jpg" alt="">
            <div class="overlay"> Image 5 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa6.jpg" alt="">
            <div class="overlay"> Image 6 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa7.jpg" alt="">
            <div class="overlay"> Image 7 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa8.jpg" alt="">
            <div class="overlay"> Image 8 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa9.jpg" alt="">
            <div class="overlay"> Image 9 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa10.jpg" alt="">
            <div class="overlay"> Image 10 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa11.jpg" alt="">
            <div class="overlay"> Image 11 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa12.jpg" alt="">
            <div class="overlay"> Image 12 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa13.jpg" alt="">
            <div class="overlay"> Image 13 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa14.jpg" alt="">
            <div class="overlay"> Image 14 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa15.jpg" alt="">
            <div class="overlay"> Image 15 </div>
        </div>

       
            <div class="gallery-item"> 
            <img src="@/assets/pessoa16.jpg" alt="">
            <div class="overlay"> Image 16 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa17.jpg" alt="">
            <div class="overlay"> Image 8 </div>
        </div>

        
            <div class="gallery-item"> 
            <img src="@/assets/pessoa18.jpg" alt="">
            <div class="overlay"> Image 18 </div>
        </div>

    </div>
    
</template>

<style scoped>
    .gallery {
    position: relative;
    /*display: inline block; */
    display: flex; 
    flex-wrap: wrap;
    justify-content: center;
    padding: 20px;
}

.gallery-item {
    position: relative;
    width: 120px;
    height: 120px;
    margin: 2px;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
}

.gallery-item img {
    width: 100%;
    height: 100%;
    transition: transform 0.4s ease;
    position: absolute; /* Torna a imagem um plano de fundo, permitindo que o overlay fique sobre ela */
    top: 0;
    left: 0;
}

.overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    opacity: 0;
    transition: opacity 0.3s ease;
    color: #fff;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.gallery-item:hover img {
    transform: scale(1.1);
}

.gallery-item:hover .overlay {
    opacity: 1;
}

</style>