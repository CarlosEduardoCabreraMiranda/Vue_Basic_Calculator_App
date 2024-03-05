<template>
    <div class="about">
        <h1 class="abtTitle">About</h1>
        <h3 id="subtitle">La aplicacion fue desarrollada en un promedio de x dias. </h3>
    </div>
    <div class="aboutLeft">
        <h3>Se hicieron modulos de:</h3>
        <div class="about-modules">
            <button class="btn btn-primary">Suma</button>
            <button class="btn btn-primary">Resta</button>
            <button class="btn btn-primary">División</button>
            <button class="btn btn-primary">Multiplicación</button>
        </div>

        <h3>Y fue hecho en colaboración con:</h3>
        <div class="about-people">
            <p>Carlos Eduardo Cabrera Miranda</p>
            <p>Alvaro Felipe Avila Vidal</p>
            <p>Juan Jose Urbano Perdomo</p>
            <img src="">
            <p>Yhonathan Camilo</p>
            <p>Nicolas Alejandro Ruiz</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'About_app',
    props: {
    }
}
</script>

<style>
.abtTitle{
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-style: italic;
}

.about {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 6px;
    margin-bottom: 5%;
}

.about-modules {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-size: 40px;
    gap: 30px;
    margin-right: 8%;
}

.about-people {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-size: 4vh;
    gap: 30px;
    margin-right: 8%;
}
.aboutLeft{
    display: flex;
    flex-direction: column;
    text-align: start;
    margin-left: 5%;
    gap: 100px;
}

</style>