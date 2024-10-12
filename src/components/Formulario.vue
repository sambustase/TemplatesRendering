<template>
    <div :class="{container: true }">
        <form :class="{box: true }" >
            <div :class="{boxInput:true}">
                <label>Color de Fondo</label>
                <input type="text" v-model="colorFondo">
            </div>
            <div :class="{boxInput:true}">
                <label>Color de texto</label>
                <input type="text" v-model="colorTexto">
            </div>
            <div :class="{boxInput:true}">
                <input type="checkbox" v-model="mostrarTexto">Mostrar texto
            </div>
            <div :class="{boxInput:true}">
                <label>Borde</label>
                <input type="range" v-model="borde">
            </div>
            <div :class="{boxInput:true}">
                <label>Contenido Textual</label>
                <textarea type="text" v-model="text"></textarea>
            </div>
            <div :class="{boxInput:true}">
                <label for="options">Tipográfia</label>
                <select v-model="tipografia" id="options">
                    <option v-for="option in options" :key="option.value" :value="option.value">{{ option.valor }}</option>
               </select> 
            </div>
            <!-- <div>
                <input type="checkbox" v-model="opacidad">Opaco
            </div> -->
            <div :class="{ boxInput: true }">
                <label>Tamaño de Letra</label>
                <div>
                    <input type="radio" v-model="tamanoLetra" value="pequeño" id="pequeño">
                    <label for="pequeño">Pequeño</label>
                    <input type="radio" v-model="tamanoLetra" value="mediano" id="mediano">
                    <label for="mediano">Mediano</label>
                    <input type="radio" v-model="tamanoLetra" value="grande" id="grande">
                    <label for="grande">Grande</label>
                </div>
            </div>
        </form>
        <div :style="{color: colorTexto, 
            backgroundColor: colorFondo,
            borderRadius: borde + 'px',
            fontStyle: tipografia,
            fontSize: tamanoLetra === 'pequeño' ? '12px' : tamanoLetra === 'mediano' ? '16px' : '20px'}" :class="{boxText: true }">
            <h1 v-show="mostrarTexto">{{ text }}</h1>
        </div>
    </div>
</template>
<script>
export default {
    name:'app',
    data(){
        return{
            colorFondo:"",
            colorTexto:"",
            mostrarTexto:true,
            borde:"",
            text:"",
            tipografia:"normal",
            tamanoLetra: "",
            // opacidad:false,
            options: [
                {value: 'normal', valor:'Normal'},
                {value: 'italic', valor:'Italic'},
                {value: 'oblique', valor:'Oblique'}
            ]
        }
    }   
}
</script>

<style scoped>
.container{
    display: flex;
}
.box{
    border: solid;
    background-color: rgb(17, 58, 74);
    margin-right: 50px ;
    color: white;
    padding: 40px;
}    
.boxText{
    width: 300px;
    height: 300px;
    display: flex;
    align-items: center
   
}
.boxInput{
    display: flex;
    flex-direction: column;
    margin-bottom: 10px;
    align-items: start;
    font-style: o ;
}
</style>