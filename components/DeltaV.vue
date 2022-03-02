<template>
  <div class="fs20r">
    <b-card class="bgcolor-pr m-3 fs20r he-800">
      <h2>デルタVの算出</h2>

      <div class="inline-block bgcolor-se position-relative shadow1 p-0 br-5"
              :class="m1.positionX + ' ' + m1.positionY"
      >
        <div class="bgcolor-fo p-4 brt-5 "
             draggable="true"
             @dragstart="dragstart('m1', $event)"
             @dragend="dragend('m1', $event)"
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
      test: 0,

      Mstart: 10,
      Mend: 1,
      Isp: 280,

      deltaV: 0,
      gravity: 9.81,

      m1: {
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
      },

      m: {
        firstX: 0,
        firstY: 0,
      }
    };
  },

  computed: {

  },

  methods: {
    dragstart: function(m, event) {
      this[m].firstX = event.pageX
      this[m].firstY = event.pageY
    },
    dragend: function(m, event) {
      this[m].endX = event.pageX
      this[m].endY = event.pageY
      this[m].diffX = this[m].endX - this[m].firstX
      this[m].diffY = this[m].endY - this[m].firstY
      this[m].posX = this[m].posX + this[m].diffX
      this[m].posY = this[m].posY + this[m].diffY
      this[m].positionX = 'lf-' + this[m].posX
      this[m].positionY = 'tp-' + this[m].posY
    }
  },

};
</script>

<style>
</style>