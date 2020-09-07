<template>
<div v-bind:style="styleObject" id="content">
    <div>
        <img :src="pokemon.sprite" alt />
    </div>
    <div>
        <h1>{{num}} - {{name | upper}}</h1>
    </div>
    <div id="type">
        <div v-for="(type, index) in pokemon.types" :key="index">
            <Type :type="type.type.name" />
        </div>
    </div>
</div>
</template>

<script>
import Type from "./Type";
import axios from "axios";
export default {
    created: function () {
        axios.get(this.url).then((resp) => {
            this.pokemon.types = resp.data.types;
            let name = this.name.replace("-", "_");
            name = name.replace("mr_", "mr._");
            name = name.replace("ho_oh", 'ho-oh')
            name = name.replace("deoxys_normal", 'deoxys')
            name = name.replace("wormadam_plant", 'wormadam')
            name = name.replace("porygon_z", 'porygon-z')
            name = name.replace("giratina_altered", 'giratina')
            name = name.replace("shaymin_land", 'shaymin')
            name = name.replace("basculin_red-striped", 'basculin')
            name = name.replace("darmanitan_standard", 'darmanitan')
            name = name.replace("tornadus_incarnate", 'tornadus')
            name = name.replace("thundurus_incarnate", 'thundurus')
            name = name.replace("landorus_incarnate", 'landorus')
            name = name.replace("keldeo_ordinary", 'keldeo')
            name = name.replace("meloetta_aria", 'meloetta')
            name = name.replace("meowstic_male", 'meowstic')
            name = name.replace("aegislash_shield", 'aegislash')
            name = name.replace("pumpkaboo_average", 'pumpkaboo')
            this.pokemon.sprite = `https://www.pkparaiso.com/imagenes/xy/sprites/animados/${name}.gif`;
            console.log(this.pokemon);
        });
    },

    data() {
        return {
            pokemon: {
                types: [],
                sprite: "",
            },
            styleObject: {
                color: "red",
                fontSize: "20px",
                height: "300px",
                display: "flex",
                justifyContent: "flex-end",
                flexDirection: "column",
            },
        };
    },
    props: {
        name: String,
        url: String,
        num: Number,
    },
    filters: {
        upper: function (value) {
            let newName = value[0].toUpperCase() + value.slice(1);
            return newName;
        },
    },
    components: {
        Type,
    },
};
</script>

<style>
#content {
    background: url("../assets/pokeball.png") no-repeat center;
    background-size: contain;
    border-radius: 5px;

    padding-bottom: 10px;
    -webkit-box-shadow: 0px 0px 3px 0px rgba(0, 0, 0, 0.41);
    -moz-box-shadow: 0px 0px 3px 0px rgba(0, 0, 0, 0.41);
    box-shadow: 0px 0px 3px 0px rgba(0, 0, 0, 0.41);
}

#type {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
