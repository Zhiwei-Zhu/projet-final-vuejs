<template>
  <v-app >
          <v-app-bar
                  app
                  v-bind:color="switch1==false ? 'grey lighten-5':'black'"
          >
              <div class="row d-flex justify-center">
                  <v-img
                          alt="fairytail Logo"
                          max-height="auto"
                          max-width="150px"
                          src="https://cdn.freelogovectors.net/wp-content/uploads/2012/03/fairy_tail-logo.png"
                          transition="scale-transition"
                  />
              </div>
          </v-app-bar>


    <v-content v-bind:class="switch1==false ? 'grey lighten-5 black--text':'black white--text '">
        <v-parallax
                height="200"
                src="https://www.animepilipinas.com/wp-content/uploads/2019/07/Fairy-Tail-Final-Series-visual-3-696x464.jpg"

        >
            <v-switch v-model="switch1" color="black"></v-switch>
            <div  class="container text-center">
                <h1>Wiki Fairy Tail</h1>
            </div>
        </v-parallax>
        <div  class="container text-center" >
            <h2>{{titlepart[0]| Upper}}</h2>
            <p>Fairy Tail est un shōnen manga écrit et dessiné par Hiro Mashima. Il est prépublié dans l’hebdomadaire Weekly Shōnen Magazine de l’éditeur Kōdansha entre le 2 août 2006 et le 27 juillet 2017 au Japon, et est compilé en un total de soixante-trois tomes. En France, en Suisse romande et en Belgique, le manga est publié en intégralité par Pika Édition entre le 10 septembre 2008 et le 27 juin 2018, Fairy Tail est aussi disponibles sur des chaines télé et des applications. (comme Netflix)</p>
            <h2>{{titlepart[1]| Upper}}</h2>
            <p>Dans le royaume de Fiore, il existe parmi le commun des mortels des hommes et des femmes qui manipulent la magie : ils sont appelés mages. Pour mieux les contrôler, des guildes — endroits où les mages se réunissent et font des travaux afin de gagner des joyaux (monnaie de Fiore) — ont été créées et mises sous la responsabilité du conseil de la magie (par l’intermédiaire des maîtres de guildes).

                Outre la nécessité de contrôler des mages, ce réseau a d’autres utilités. En effet, il permet de fournir un large choix de mages au client, et de nombreuses missions aux mages par le biais de petites annonces.

                Parmi les nombreuses guildes, une d’entre elles fait particulièrement parler d’elle, que ce soit par les actes réalisés par ses membres, mais aussi et surtout pour les dégâts matériels provoqués par ces derniers à chaque mission qu’ils effectuent. Il s’agit de Fairy Tail.</p>
            <h2>{{titlepart[2]| Upper}}</h2>
            <p>L’histoire se focalise principalement sur les missions effectuées par l’une des équipes de Fairy Tail, composée de Natsu Dragnir (chasseur de dragon de feu), Lucy Heartfilia (constellationniste) et Happy (un chat bleu Exceed pouvant se faire pousser des ailes, voler et parler), qui seront très vite rejoints par Erza Scarlett (mage chevalier) et Grey Fullbuster (Mage de glaces puis plus tard Chasseur de démons de Glace), deux autres membres de la fameuse guilde. Ils sont rejoints au cours de l'aventure par Carla (une chatte blanche Exceed, comme Happy), Wendy (chasseuse de dragon céleste) et par bien d'autres.</p>
        </div>
        <div  class="container text-center">
            <h2>{{titlepart[3]| Upper}}</h2>
        <div class="row" >
            <div class="col-sm-4" v-bind:key="cardlist" v-for="cardlist in cardlists">
                <character v-bind:name="cardlist.name" :description="cardlist.description" :img="cardlist.img"></character>
            </div>
        </div>
            <v-card>
                <h2>{{titlepart[4]| Upper}}</h2>
                <v-form class="row justify-center">
                    <div class="col-5">
                        <v-text-field
                                v-model="object.name"
                                label="name"
                                required
                        ></v-text-field>
                    </div>
                    <div class="col-5">
                        <v-rating color="orange" background-color="orange lighten-3" v-model="object.rate"></v-rating>
                    </div>
                    <div class="col-10">
                        <v-textarea v-model="object.comment"
                                    label="comment"
                                    required>  </v-textarea>
                    </div>
                    <div class="col-12">
                        <v-btn v-on:click="addobj">Validate</v-btn>
                    </div>
                </v-form>
            </v-card>
        </div>
        <div class="container" v-bind:key="object" v-for="object in arrayobject" v-bind:class="switch1==true?'white--text':'black--text'">
            <div class="row justify-center" v-if="arrayobject.length>0">
                <div class="col-5">
                    <h4>{{object.name}}</h4>
                </div>
                <div class="col-5">
                    <v-rating color="orange" background-color="orange lighten-3" v-bind:value="object.rate" readonly ></v-rating>
                </div>
                <div class="col-10">
                    <p>{{object.comment}}</p>
                </div>
            </div>
            <div v-else>
                <p>il n'y a pas de commentaire.</p>
            </div>
        </div>
    </v-content>
  </v-app>
</template>

<script>
    import character from "./components/character";

export default {
  name: 'App',

  components: {
      character,
  },

  data: () => ({
      titlepart:['Résumé','Prologue','Sypnosis','Personnages','Commentaire'],
      switch1:false,
      cardlists:[
          {
              name:'Natsu Dragneel',
              description:'Natsu est un mage faisant partie de la guilde de Fairy Tail. Il fut élevé par un dragon ( Igneel ) qui lui enseigna la magie. C\'est ainsi qu\'il est devenu un Dragon Slayer de feu ( pouvoir qui peut tuer les dragons ). Ce manieur de flammes est l\'un des mages les plus forts de Fairy Tail.',
              img:'https://vignette.wikia.nocookie.net/five-world-war/images/1/17/Igneel_wallpaper.png/revision/latest?cb=20180518055918',
          },
          {
              name:'Lucy Heartfilia',
              description:'Lucy Heartfilia (?) (ルーシイ・ハートフィリア, Rūshi Hatofiria) est une Mage Constellationniste de Fairy Tail, utilisant la Magie des Constellations. Elle est la riche héritière de la famille Heartfilia, fille de Jude et Layla. Elle a perdu sa mère étant enfant et son père plus tard',
              img:'https://i.pinimg.com/originals/01/70/14/017014bfc3fa1423364ae1c63209f8fb.jpg',
          },
          {
              name:'Gray Fullbuster',
              description:'Grey Fullbuster  (?) (グレイ・フルバスター, Gurei Furubasutâ) est l\'un des Mages les plus puissants de la Guilde Fairy Tail ; il fait partie de l\'Équipe de Natsu. Il pratique la Magie de Glace Constructive, qui lui a été enseignée par Oul, en compagnie de Leon Bastia, jusqu\'à ce que Grey entre dans la Guilde Fairy Tail, à la suite de la disparition d\'Oul (son maître de magie). Il est devenu un Chasseur de Démon de Glace, suite à la mort de son père qui lui a donné ses pouvoirs. Il est le fils de Mika Fullbuster et de Silver.',
              img:'https://vignette.wikia.nocookie.net/fairy-tail/images/d/dc/Grey%2C_membre_d%27Avatar_anime.png/revision/latest/scale-to-width-down/350?cb=20181021231819&path-prefix=fr',
          },
      ],
      arrayobject:[],
      object:{
          name:'',
          comment:'',
          rate: 0,
      },
  }),
    filters:{
        Upper : function (value) {
            return value.toUpperCase();
        }
    },
    mounted() {
        if(localStorage.getItem('arrayobject')) {
            try {
                this.arrayobject = JSON.parse(localStorage.getItem('arrayobject'));
            } catch(e) {
                localStorage.removeItem('arrayobject');
            }
        }
    },
    methods:{
        addobj() {
            if(!this.object) return;
            this.arrayobject.push(this.object);
            this.object = '';
            this.saveobj();
        },
        saveobj() {
            let parsed = JSON.stringify(this.arrayobject);
            localStorage.setItem('arrayobject', parsed);
        }
    }
};

</script>
<style>
    h1{
        margin-top: 50px;
    }
    h2{
        padding-top: 25px;
    }
</style>
