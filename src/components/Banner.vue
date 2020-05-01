<template>
    <section class="home-banner">
        <v-container>
            <div class="d-flex justify-center align-center">
                <v-icon large style="width:200px; height:200px;" class="mr-10">$logo</v-icon>
                <h1>Hi <br> I'm Mohammed Shameem <br> and I am a UI Developer</h1>
            </div>
        </v-container>
    </section>
</template>

<style lang="scss" scoped>
.home-banner{
    // height: 100vh;
    display: flex;
    align-items: center;
}
h1{
    font-size: 4.5rem;
    text-align: center;
    @media (max-width: 1199px){
        font-size: 3rem;
    }
}
.theme--dark svg{
    fill: #fff;
}
</style>