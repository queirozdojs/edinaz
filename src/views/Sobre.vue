<template>
  <div id="sobre">
    <h1>Personagens suspeitos</h1>
    <br>

    <div v-for="personagem in personagens" :key="personagem.id" class="personagem">
      <img :src="personagem.thumbnail.path + '.' + personagem.thumbnail.extension" alt="Imagem do personagem" width="15%">
      <br>
      <strong>{{ personagem.name }}</strong>
      <br>
      <p>{{ personagem.description }}<br></p>
    </div>
  </div>
</template>

<style>
#sobre {
  text-align: center;
  background-color: #000000;
  padding: 20px;
  color: white;
}

.personagem {
  margin-bottom: 20px;
}

.personagem img {
  border-radius: 20%;
}

.personagem strong {
  font-size: 18px;
  margin-top: 10px;
}

.personagem p {
  font-size: 14px;
  margin-bottom: 10px;
}
</style>
<script>
import md5 from 'md5'
import axios from 'axios'
export default {
    name: 'sobre-view',
    data(){
        return{
            ts: Date.now(),
            chave_publica: 'eaab8e7dc36244dde64894302b6b9945',
            chave_privada: '2db2c83d49939f0677f3f765680d01b51cd12dd6',
            hash: md5(this.ts+this.chave_privada+this.chave_publica),
            personagens: []
        }
    },
    mounted(){
        axios.get("http://gateway.marvel.com/v1/public/characters?ts="+this.ts+"&apikey="+this.chave_publica+"&hash="+md5(this.ts+this.chave_privada+this.chave_publica))
        .then(res => {
            console.log(res)
            this.personagens = res.data.data.results
        })
    }
}
</script>
