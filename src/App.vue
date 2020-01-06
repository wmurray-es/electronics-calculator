<template>
  <div id="app">
    <section class="section">
      <!--<div>
        <label>
          Required milliamps
          <input type="number" v-model.number="milliamps" class="input is-small">
        </label>
      </div>-->
      <div>
        <label>
          Required milliwatts
          <input
            type="number"
            v-model.number="milliwatts"
            class="input is-small"
          >
        </label>
      </div>

      <div>
        <label>
          Required voltage
          <input
            type="number"
            v-model.number="requiredVoltage"
            class="input is-small"
          >
        </label>
      </div>

      <div>
        <label>
          Supplied voltage
          <input
            type="number"
            v-model.number="suppliedVoltage"
            class="input is-small"
          >
        </label>
      </div>
    </section>

    <section class="section">
      <table class="table">
        <tr>
          <th>Power</th>
          <td>
            {{ wattsCalculated }}
            <span class="muted">Watts</span>
          </td>
        </tr>
        <tr>
          <th>Current</th>
          <td>
            {{ ampsCalculated }}
            <span class="muted">Amps</span>
          </td>
        </tr>
        <tr>
          <th>Resistance</th>
          <td>
            {{ ohmsCalculated }}
            <span class="muted">Ohms</span>
          </td>
        </tr>
      </table>
    </section>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    milliamps: 0,
    milliwatts: 40,
    requiredVoltage: 3.3,
    suppliedVoltage: 5
  }),
  computed: {
    wattsCalculated() {
      return this.milliwatts / 1000;
    },
    ampsCalculated() {
      return this.wattsCalculated / this.suppliedVoltage;
    },
    ohmsCalculated() {
      return this.suppliedVoltage / this.ampsCalculated;
    }
  }
};
</script>

<style>
.muted {
  opacity: 0.5;
}
</style>
