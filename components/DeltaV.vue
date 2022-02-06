<template>
  <div class="fs20r">
      <b-card class="bgcolor-pr m-3 fs20r">
        <h2>デルタVの算出</h2>
        <b-form @submit="onSubmit" v-if="show">
          <b-form-group
            label-for="input-1"
            class="pt-4"
          >
            <p>
              スタート重量:※トン数 半角数字
              <b-form-input
                v-model="form.Mstart"
                type="number"
                step="0.001"
                required
                class="fs16r"
              ></b-form-input>
            </p>
            <p>
              エンド重量:※トン数 半角数字
              <b-form-input
                v-model="form.Mend"
                type="number"
                step="0.0000000000001"
                required
                class="fs16r"
              ></b-form-input>
            </p>
            <p>
              比推力:※秒 半角数字
              <b-form-input
                v-model="form.Isp"
                type="number"
                step="0.01"
                required
                class="fs16r"
              ></b-form-input>
            </p>
          </b-form-group>
          <b-button type="submit" variant="primary" class="fs16r">計算</b-button>
        </b-form>
        <p>DeltaV: {{deltaV}}</p>
      </b-card>
  </div>
</template>


<script>
export default {
    data() {
      return {
        form: {
          Mstart: 10,
          Mend: 1,
          Isp: 280,
        },
        show: true,
        
        deltaV: 0,
        gravity: 9.81,
      }
    },

    methods: {
      onSubmit(event) {
        event.preventDefault();
        this.deltaV = Math.log(this.form.Mstart / this.form.Mend) * this.form.Isp * this.gravity;
      },
    }
}
</script>

<style>

</style>