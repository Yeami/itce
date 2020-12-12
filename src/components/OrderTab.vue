<template>
  <div class="order-tab">
    <span style="font-size: 1.25rem; font-weight: bold; margin-right: 2rem">Заказ</span>
    <a-button @click="calc">Сформировать заказ</a-button>

    <div class="block">
      <div class="subblock">
        <span>Корпуса (тип)</span>
        <span>KA</span>
        <span>KB</span>
        <span>KC</span>
        <span>Итого</span>
      </div>
      <div class="subblock" style="margin-left: 1rem">
        <span>Коробок (шт)</span>
        <span>{{ KA_Corps_Boxes }}</span>
        <span>{{ KB_Corps_Boxes }}</span>
        <span>{{ KC_Corps_Boxes }}</span>
        <span>{{ KA_Corps_Boxes + KB_Corps_Boxes + KC_Corps_Boxes }}</span>
      </div>
    </div>

    <div class="block">
      <div class="subblock">
        <span>Лента (тип)</span>
        <span>LA</span>
        <span>LB</span>
        <span>LC</span>
        <span>Итого</span>
      </div>
      <div class="subblock" style="margin-left: 1rem">
        <span>Коробок (шт)</span>
        <span>{{ LA_Rolls_Boxes }}</span>
        <span>{{ LB_Rolls_Boxes }}</span>
        <span>{{ LC_Rolls_Boxes }}</span>
        <span>{{ LA_Rolls_Boxes + LB_Rolls_Boxes + LC_Rolls_Boxes }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'OrderTab',
  props: {
    getCorpsBoxes: Function,
    getRollsBoxes: Function,
  },
  data() {
    return {
      KA_Corps_Boxes: 0,
      KB_Corps_Boxes: 0,
      KC_Corps_Boxes: 0,
      LA_Rolls_Boxes: 0,
      LB_Rolls_Boxes: 0,
      LC_Rolls_Boxes: 0,
    };
  },
  methods: {
    calc() {
      this.getCorpsBoxesAmount();
      this.getRollsBoxesAmount();
    },
    getCorpsBoxesAmount() {
      const data = this.getCorpsBoxes();
      this.KA_Corps_Boxes = data[0];
      this.KB_Corps_Boxes = data[1];
      this.KC_Corps_Boxes = data[2];
    },
    getRollsBoxesAmount() {
      const data = this.getRollsBoxes();
      this.LA_Rolls_Boxes = data[0];
      this.LB_Rolls_Boxes = data[1];
      this.LC_Rolls_Boxes = data[2];
    }
  }
}
</script>

<style scoped lang="scss">
.block {
  display: flex;
  margin-top: 1rem;
  align-items: center;
  justify-content: center;
  border: 1px solid black;

  .subblock {
    display: flex;
    flex-direction: column;
  }
}
</style>