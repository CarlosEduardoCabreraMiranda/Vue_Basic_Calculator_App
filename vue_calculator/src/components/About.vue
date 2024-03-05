<template>
    <div class="about">
        <h1 class="abtTitle">About</h1>
        <h3 id="subtitle">La aplicacion fue desarrollada durante el periodo de tiempo anterior a la presentación de la misma.
            Esperamos sea de su agrado </h3>
    </div>
    <div class="aboutLeft">
        <h3>Se hicieron modulos de:</h3>
        <div class="about-modules">
            <button class="btn btn-primary">Suma</button>
            <button class="btn btn-secondary">Resta</button>
            <button class="btn btn-danger">División</button>
            <button class="btn btn-info">Multiplicación</button>
        </div>
        <div class="about-last-two-modules">
            <button class="btn btn-dark">Porcentaje</button>
            <button class="btn btn-warning">Parentesis</button>
        </div>


        <h3 class="subtitle-people">Y fue hecho en colaboración con:</h3>
        <div class="about-people">
            <p>{{ DevA }}</p>
            <p>{{ DevB }}</p>
            <p>{{ DevC }}</p>
        </div>

        <div class="about-last-two">
            <p>{{ DevD }}</p>
            <p>{{ DevE }}</p>
        </div>

    </div>
</template>

<script>
export default {
    name: 'About_app',
    props: {
        DevA: String,
        DevB: String,
        DevC: String,
        DevD: String,
        DevE: String,
    }
}
</script>

<style>
.abtTitle {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-style: italic;
}

.about {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    text-align: center;
    gap: 6px;
    margin-bottom: 5%;
}

.subtitle-people{
    font-style: oblique;
    font-weight: bold;
}

.about-modules {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-size: 40px;
    gap: 30px;
    margin-right: 8%;
}

.about-last-two-modules {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-size: 4vh;
    gap: 10px;
    margin-right: 8%;
    gap: 30px;
}

.about-people {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-size: 4vh;
    gap: 30px;
    margin-right: 8%;
}

.about-people:hover,
.about-last-two:hover,
.about-modules:hover,
.about-last-two-modules:hover,
.subtitle-people:hover {
    transform: scale(1.1);
}

.about-last-two {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-size: 4vh;
    gap: 10px;
    margin-right: 8%;
    gap: 30px;
}

.aboutLeft {
    display: flex;
    flex-direction: column;
    text-align: center;
    margin-left: 5%;
    gap: 100px;
}
</style>