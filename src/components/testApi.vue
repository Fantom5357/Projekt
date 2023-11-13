<template>
    <div class="homebg text">
        <h1>Точно первый в мире чат</h1>
        <p>Ъ</p>
        <div>
            <h4>Тестовые Api(По приколу)</h4>
            <div v-if="isLoad"></div>
            <div v-else>
                <div v-for="el in  teamData" :key="el.id">
                    {{ el.id }}. {{ el.abbreviation }} {{ el.city }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TestApi',
    data(){
        return{
        teamData: [],
        isLoad: true
        }
    },
    mounted(){
        const url = 'https://free-nba.p.rapidapi.com/teams?page=0';
        const options = {
            method: 'GET',
            headers: {
                'X-RapidAPI-Key': 'd4f9d16794msh78cc6858d7a1075p17ba17jsn37c18abeabb9',
                'X-RapidAPI-Host': 'free-nba.p.rapidapi.com'
            }
};
        fetch(url, options)
        .then((res) => res.json())
        .then((res) => {
            console.log(res);
            this.teamData = res.data
            this.isLoad = false
        })
}
}

</script>