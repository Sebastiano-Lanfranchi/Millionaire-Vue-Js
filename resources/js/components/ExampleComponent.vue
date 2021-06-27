<template>
    <div class="container-box mt-5">
        <div class="container-box-question">
           <div class="box-question col-md-12"  id="app">
              {{questionsandanswers[p].question}}
           </div>
        </div>
        <div class="container-box-answer row">
            <input type="button" v-for="item in questionsandanswers[p].answers"  v-on:click="switchQuestion(); controlAnswer(item)" :key="item.answers"  :value="item" class="box-answer col-md-6 mt-3">
        </div>
    </div>
</template>
<script>
 export default {

        data: function(){
          return {
              questionsandanswers: [
               {
                   question: 'Come mi chiamo?',

                   answers: [
                       'Gigio',
                       'Ernesto',
                       'Sebastiano',
                       'Luca'
                   ]
                },
               {
                   question: 'Le mucche sono?',

                   answers: [
                        'Mammiferi',
                        'Anfibi',
                        'Rettili',
                        'Marsupiali'
                   ]

                },
                {
                   question: "Qual'é l'elemento piú luminoso del universo? ",

                   answers: [
                        'Quasar',
                        'SuperNova',
                        'Buco Nero',
                        'Galassia'
                   ]

                }
              ],

              p: 0,
              i: '',
              point: 0,
              indexOfQuestion:[],
              correctAnswers:['Mammiferi', 'Sebastiano', 'Quasar'],

            }
        },
        mounted(){
            const self = this;
            for(self.i=0; self.i < Object.keys(self.questionsandanswers).length; self.i++){
               self.indexOfQuestion.push(self.i)
            }

            self.questionsandanswers.sort(() => Math.random() - 0.5);
},
        methods: {
         switchQuestion: function(){
             if(this.indexOfQuestion.length-1 > this.p){
                this.p++
             }else if(this.indexOfQuestion.length > this.p){
                 alert('Le domande sono finite, hai totalizzato'+ this.point + 'punti')
             }

         },
         controlAnswer: function(item){
           if(this.correctAnswers.includes(item)){
             return this.point++

           }
         }
        }
     }
</script>

