<template>
  <div class="fs20r">
    <b-card class="bgcolor-pr m-3 fs20r he-100">
      <h2>デルタVの算出</h2>
      <div class="inline-block bgcolor-se position-relative shadow1 p-0 br-5"
              :class="positionX + ' ' + positionY"
      >
        <div class="bgcolor-fo p-4"
             draggable="true"
             @dragstart="dragstart"
             @dragend="dragend"
        ></div>
        <div>
          <table class="m-3">
            <tr>
              <th>スタート重量:</th>
              <td><input type="text" v-model="Mstart"></td>
            </tr>
            <tr>
              <th>エンド重量:</th>
              <td><input type="text" v-model="Mend"></td>
            </tr>
            <tr>
              <th>比推力:</th>
              <td><input type="text" v-model="Isp"></td>
            </tr>
            <tr>
              <th>DeltaV:</th>
              <td>{{ Math.log(Mstart / Mend) * Isp * gravity }}</td>
            </tr>
          </table>
        </div>
      </div>
    </b-card>
  </div>
</template>


<script>
export default {
  data() {
    return {
      Mstart: 10,
      Mend: 1,
      Isp: 280,

      deltaV: 0,
      gravity: 9.81,

      firstX: 0,
      firstY: 0,
      endX: 0,
      endY: 0,
      diffX: 0,
      diffY: 0,
      posX: 0,
      posY: 0,
      positionX: '',
      positionY: '',
    };
  },

  computed: {

  },

  methods: {
    dragstart: function(event) {
      this.firstX = event.pageX
      this.firstY = event.pageY
    },
    dragend: function(event) {
      this.endX = event.pageX
      this.endY = event.pageY
      this.diffX = this.endX - this.firstX
      this.diffY = this.endY - this.firstY
      this.posX = this.posX + this.diffX
      this.posY = this.posY + this.diffY
      this.positionX = 'lf-' + this.posX
      this.positionY = 'tp-' + this.posY
    }
  },

};
</script>

<style>
</style>