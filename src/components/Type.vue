<template>
<div v-bind:style="typeStyle" id="content">
    <p>{{name}}</p>
</div>
</template>

<script>
export default {
    created: function () {
        this.name = this.type.toUpperCase()
        switch (this.type) {
            case 'electric':
                this.typeStyle.background = '#F5CB50'
                break
            case 'normal':
                this.typeStyle.background = '#dedede'
                break
            case 'ground':
                this.typeStyle.background = '#7B4F2C'
                break
            case 'poison':
                this.typeStyle.background = 'purple'
                break
            case 'grass':
                this.typeStyle.background = '#87BD29'
                break
            case 'fire':
                this.typeStyle.background = '#C8101A'
                break
            case 'flying':
                this.typeStyle.background = '#20A3E9'
                break
            case 'water':
                this.typeStyle.background = '#5284E6'
                break
            case 'bug':
                this.typeStyle.background = '#A5AD1B'
                break
            case 'fairy':
                this.typeStyle.background = '#E0B1E5'
                break
            case 'fighting':
                this.typeStyle.background = '#753A33'
                break
            case 'psychic':
                this.typeStyle.background = '#DF4E7A'
                break
            case 'rock':
                this.typeStyle.background = '#B8A35A'
                break
            case 'steel':
                this.typeStyle.background = '#999AAE'
                break
            case 'ice':
                this.typeStyle.background = '#77D2ED'
                break
            case 'ghost':
                this.typeStyle.background = '#55589B'
                break
            case 'dark':
                this.typeStyle.background = '#666'
                break
            default:
                this.typeStyle.background = 'blue'
        }
    },

    data() {
        return {
            typeStyle: {
                background: 'red',
                width: '100px',
                color: 'white',
                display: 'flex',
                justifyContent: 'center',
                alignItems: 'center',
                height: ' 30px',
                fontWeight: 'bold',
                padding: '5px',
                fontSize: '16px',
                margin: '10px',
                borderRadius: '20px',
            },
            name: ''
        };
    },
    props: {
        type: String,
    },
    filters: {
        upper: function (value) {
            let newName = value[0].toUpperCase() + value.slice(1);
            return newName;
        },
    },
};
</script>

<style>

</style>
