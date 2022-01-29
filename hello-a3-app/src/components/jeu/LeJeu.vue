<template>
  <div>
    <table>
      <tr>
        <th>
          <Lacase
            :id="plateau.case[0].id"
            :image="plateau.case[0].image"
            @clickCase="traiteClick"
          />
        </th>
        <th>
          <Lacase
            :id="plateau.case[1].id"
            :image="plateau.case[1].image"
            @clickCase="traiteClick"
          />
        </th>
      </tr>
    </table>
  </div>
</template>

<script>
import Lacase from "@/components/jeu/LaCase.vue";
export default {
  components: {
    Lacase,
  },
  data() {
    return {
      plateau: {
        case: [
          { id: "1", image: "", state: 0 },
          { id: "2", image: "", state: 0 },
        ],
      },
    };
  },
  methods: {
    traiteClick(idcase) {
      console.log("Case clicquée :" + idcase);
      Object.keys(this.plateau.case).forEach((cse) => {
        if (idcase == this.plateau.case[cse].id) {
          switch (this.plateau.case[cse].state) {
            case 0:
              this.plateau.case[cse].state = 1;
              this.plateau.case[cse].image = "f1";
              break;
            case 1:
              this.plateau.case[cse].state = 2;
              this.plateau.case[cse].image = "ours";
              break;
            case 2:
              this.plateau.case[cse].state = 0;
              this.plateau.case[cse].image = "";
          }
        }
      });
    },
  },
};
</script>