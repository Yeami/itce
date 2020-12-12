<template>
  <div class="wrapper-component">
    <a-tabs default-active-key="1">

      <a-tab-pane key="1" tab="Кратность">
        <multiplicity-tab
            :inOneContainerBoxesCorps="inOneContainerBoxesCorps"
            :inOneBoxCorps="inOneBoxCorps"
            :inOneContainerBoxesTape="inOneContainerBoxesTape"
            :inOneBoxRolls="inOneBoxRolls"
            :AKALA="AKALA"
            :AKALB="AKALB"
            :AKBLA="AKBLA"
            :AKBLC="AKBLC"
            :AKCLB="AKCLB"
        />
      </a-tab-pane>

      <a-tab-pane key="2" tab="Расчёт">
        <calculation-tab
            :AKALAAmount="AKALAAmount"
            :AKALARollsAmount="AKALARollsAmount"
            :reCalcAKALARollsAmount="reCalcAKALARollsAmount"

            :AKALBAmount="AKALBAmount"
            :AKALBRollsAmount="AKALBRollsAmount"
            :reCalcAKALBRollsAmount="reCalcAKALBRollsAmount"

            :AKBLAAmount="AKBLAAmount"
            :AKBLARollsAmount="AKBLARollsAmount"
            :reCalcAKBLARollsAmount="reCalcAKBLARollsAmount"

            :AKBLCAmount="AKBLCAmount"
            :AKBLCRollsAmount="AKBLCRollsAmount"
            :reCalcAKBLCRollsAmount="reCalcAKBLCRollsAmount"

            :AKCLBAmount="AKCLBAmount"
            :AKCLBRollsAmount="AKCLBRollsAmount"
            :reCalcAKCLBRollsAmount="reCalcAKCLBRollsAmount"

            :audioCassettesSum="audioCassettesSum"
            :rollsSum="rollsSum"

            :inOneBoxCorps="inOneBoxCorps"
            :inOneBoxRolls="inOneBoxRolls"

            :round="round"

            :AKALA="AKALA"
            :AKALB="AKALB"
            :AKBLA="AKBLA"
            :AKBLC="AKBLC"
            :AKCLB="AKCLB"

            :inOneContainerBoxesCorps="inOneContainerBoxesCorps"
            :inOneContainerBoxesTape="inOneContainerBoxesTape"

            :updateKACorpsBoxes="updateKACorpsBoxes"
            :updateKBCorpsBoxes="updateKBCorpsBoxes"
            :updateKCCorpsBoxes="updateKCCorpsBoxes"

            :updateLARollsBoxes="updateLARollsBoxes"
            :updateLBRollsBoxes="updateLBRollsBoxes"
            :updateLCRollsBoxes="updateLCRollsBoxes"
        />
      </a-tab-pane>

      <a-tab-pane key="3" tab="Заказ">
        <order-tab
            :getCorpsBoxes="getCorpsBoxes"
            :getRollsBoxes="getRollsBoxes"
        />
      </a-tab-pane>
    </a-tabs>
  </div>
</template>

<script>
import MultiplicityTab from '@/components/MultiplicityTab'
import CalculationTab from '@/components/CalculationTab'
import OrderTab from '@/components/OrderTab'

export default {
  name: 'WrapperComponent',
  components: {
    MultiplicityTab,
    CalculationTab,
    OrderTab,
  },
  computed: {
    audioCassettesSum() {
      return this.AKALAAmount + this.AKALBAmount + this.AKBLAAmount + this.AKBLCAmount + this.AKCLBAmount;
    },
    rollsSum() {
      return this.AKALARollsAmount + this.AKALBRollsAmount + this.AKBLARollsAmount + this.AKBLCRollsAmount + this.AKCLBRollsAmount;
    },
  },
  data() {
    return {
      //                КРАТНОСТЬ
      // Корпуса
      inOneContainerBoxesCorps: 975, // В одном контейнере (коробок)
      inOneBoxCorps: 200, // В одной коробке корпусов (шт)
      // Лента
      inOneContainerBoxesTape: 750, // В одном контейнере (коробок)
      inOneBoxRolls: 40, // В одной коробке (рулонов)
      // Аудиокассеты
      AKALA: 25,
      AKALB: 26,
      AKBLA: 27,
      AKBLC: 28,
      AKCLB: 29,
      //                КРАТНОСТЬ

      //                РАСЧЁТ
      AKALAAmount: 123200, // Количество AKALA кассет, которые нужно создать
      AKALARollsAmount: 0, // Количество рулонов, которые нужны для AKALA кассет

      AKALBAmount: 23450, // Количество AKALB кассет, которые нужно создать
      AKALBRollsAmount: 0, // Количество рулонов, которые нужны для AKALB кассет

      AKBLAAmount: 101500, // Количество AKBLA кассет, которые нужно создать
      AKBLARollsAmount: 0, // Количество рулонов, которые нужны для AKBLA кассет

      AKBLCAmount: 300000, // Количество AKBLC кассет, которые нужно создать
      AKBLCRollsAmount: 0, // Количество рулонов, которые нужны для AKBLC кассет

      AKCLBAmount: 400000, // Количество AKCLB кассет, которые нужно создать
      AKCLBRollsAmount: 0, // Количество рулонов, которые нужны для AKCLB кассет

      //
      KA_Corps_Boxes: 0,
      KB_Corps_Boxes: 0,
      KC_Corps_Boxes: 0,
      //
      LA_Rolls_Boxes: 0,
      LB_Rolls_Boxes: 0,
      LC_Rolls_Boxes: 0,
    }
  },
  methods: {
    updateKACorpsBoxes(amount) {
      this.KA_Corps_Boxes = amount;
    },
    updateKBCorpsBoxes(amount) {
      this.KB_Corps_Boxes = amount;
    },
    updateKCCorpsBoxes(amount) {
      this.KC_Corps_Boxes = amount;
    },
    updateLARollsBoxes(amount) {
      this.LA_Rolls_Boxes = amount;
    },
    updateLBRollsBoxes(amount) {
      this.LB_Rolls_Boxes = amount;
    },
    updateLCRollsBoxes(amount) {
      this.LC_Rolls_Boxes = amount;
    },
    round(number) {
      return Math.round((number + Number.EPSILON) * 100) / 100
    },
    reCalcAKALARollsAmount() {
      this.AKALARollsAmount = this.round(this.AKALAAmount / this.AKALA);
    },
    reCalcAKALBRollsAmount() {
      this.AKALBRollsAmount = this.round(this.AKALBAmount / this.AKALB);
    },
    reCalcAKBLARollsAmount() {
      this.AKBLARollsAmount = this.round(this.AKBLAAmount / this.AKBLA);
    },
    reCalcAKBLCRollsAmount() {
      this.AKBLCRollsAmount = this.round(this.AKBLCAmount / this.AKBLC);
    },
    reCalcAKCLBRollsAmount() {
      this.AKCLBRollsAmount = this.round(this.AKCLBAmount / this.AKCLB);
    },
    getCorpsBoxes() {
      return [this.KA_Corps_Boxes, this.KB_Corps_Boxes, this.KC_Corps_Boxes];
    },
    getRollsBoxes() {
      return [this.LA_Rolls_Boxes, this.LB_Rolls_Boxes, this.LC_Rolls_Boxes];
    }
  },
  mounted() {
    this.reCalcAKALARollsAmount();
    this.reCalcAKALBRollsAmount();
    this.reCalcAKBLARollsAmount();
    this.reCalcAKBLCRollsAmount();
    this.reCalcAKCLBRollsAmount();
  }
}
</script>

<style lang="scss">
.wrapper-component {
  width: 100%;
  height: 100vh;
}
</style>