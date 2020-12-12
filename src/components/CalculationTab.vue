<template>
  <div class="calculation-tab">

    <div class="block">
      <div class="table-titles">
        <span>Тип видеокассеты</span>
        <span>Корпус</span>
        <span>Лента</span>
        <span>Количество</span>
        <span>Рулонов</span>
      </div>

      <!-- AKALA -->
      <div class="table-row">
        <span style="margin-right: 10rem">AKALA</span>
        <span style="margin-right: 5.675rem">KA</span>
        <span style="margin-right: 5rem">LA</span>
        <a-input
            style="width: 5rem!important;"
            :value="AKALAAmount"
            @change="reCalcAKALARollsAmount"
        />
        <span style="margin-left: 4.25rem">{{ AKALARollsAmount }}</span>
      </div>

      <!-- AKALB -->
      <div class="table-row">
        <span style="margin-right: 10rem">AKALB</span>
        <span style="margin-right: 5.675rem">KA</span>
        <span style="margin-right: 5rem">LB</span>
        <a-input
            style="width: 5rem!important;"
            :value="AKALBAmount"
            @change="reCalcAKALBRollsAmount"
        />
        <span style="margin-left: 4.25rem">{{ AKALBRollsAmount }}</span>
      </div>

      <!-- AKBLA -->
      <div class="table-row">
        <span style="margin-right: 10rem">AKBLA</span>
        <span style="margin-right: 5.675rem">KB</span>
        <span style="margin-right: 5rem">LA</span>
        <a-input
            style="width: 5rem!important;"
            :value="AKBLAAmount"
            @change="reCalcAKBLARollsAmount"
        />
        <span style="margin-left: 4.25rem">{{ AKBLARollsAmount }}</span>
      </div>

      <!-- AKBLC -->
      <div class="table-row">
        <span style="margin-right: 10rem">AKBLC</span>
        <span style="margin-right: 5.675rem">KB</span>
        <span style="margin-right: 5rem">LC</span>
        <a-input
            style="width: 5rem!important;"
            :value="AKBLCAmount"
            @change="reCalcAKBLCRollsAmount"
        />
        <span style="margin-left: 4.25rem">{{ AKBLCRollsAmount }}</span>
      </div>

      <!-- AKCLB -->
      <div class="table-row">
        <span style="margin-right: 10rem">AKCLB</span>
        <span style="margin-right: 5.675rem">KC</span>
        <span style="margin-right: 5rem">LB</span>
        <a-input
            style="width: 5rem!important;"
            :value="AKCLBAmount"
            @change="reCalcAKCLBRollsAmount"
        />
        <span style="margin-left: 4.25rem">{{ AKCLBRollsAmount }}</span>
      </div>

      <!-- Sum -->
      <div class="table-row" style="border-top: 1px solid black; margin-top: 0.5rem; padding-top: 0.5rem">
        <span style="margin-left: 26.5rem">{{ audioCassettesSum }}</span>
        <span style="margin-left: 5.5rem">{{ rollsSum }}</span>
      </div>
    </div>

    <div class="block" style="margin-top: 2rem">
      <div class="table-titles">
        <span style="font-weight: bold">Корпус</span>
        <span>Корпусов (шт)</span>
        <span>Коробок (шт)</span>
      </div>

      <div class="table-row">
        <span style="margin-right: 15rem">KA</span>
        <span style="margin-right: 15rem">{{ KACorpsAmount }}</span>
        <span>{{ KACorpsBoxes() }}</span>
      </div>

      <div class="table-row">
        <span style="margin-right: 15rem">KB</span>
        <span style="margin-right: 15rem">{{ KBCorpsAmount }}</span>
        <span>{{ KBCorpsBoxes() }}</span>
      </div>

      <div class="table-row">
        <span style="margin-right: 15rem">KC</span>
        <span style="margin-right: 15rem">{{ KCCorpsAmount }}</span>
        <span>{{ KCCorpsBoxes() }}</span>
      </div>

      <!-- Sum -->
      <div class="table-row" style="border-top: 1px solid black; margin-top: 0.5rem; padding-top: 0.5rem">
        <span style="margin-left: 16rem">{{ CorpsAmountSum }}</span>
        <span style="margin-left: 15rem">{{ CorpsBoxesSum }}</span>
      </div>
    </div>
    <span style="color: red">{{ CheckCorpsBoxesSum ? 'Уменьшите или увеличьте количество корпусов' : '' }}</span>

    <div style="display: flex; flex-direction: row">
      <div class="block" style="margin-top: 2rem">
        <div class="table-titles">
          <span style="font-weight: bold">Лента</span>
          <span>Рулонов</span>
          <span>Коробок</span>
          <span>Остаток ленты (рулонов)</span>
          <span>Уменьшить/увеличить (коробок)</span>
        </div>

        <div class="table-row">
          <span>LA</span>
          <span style="margin-left: 3.5rem">{{ LARollsAmount }}</span>
          <span style="margin-left: 2.75rem">{{ LARollsBoxes() }}</span>
          <span style="margin-left: 7rem">{{ LARemainingRolls }}</span>
          <a-input
              style="width: 7rem!important; margin-left: 10rem; color: red"
              :value="LAChangeBoxes"
          />
        </div>

        <div class="table-row">
          <span>LB</span>
          <span style="margin-left: 3.5rem">{{ LBRollsAmount }}</span>
          <span style="margin-left: 2.75rem">{{ LBRollsBoxes() }}</span>
          <span style="margin-left: 7rem">{{ LBRemainingRolls }}</span>
          <a-input
              style="width: 7rem!important; margin-left: 10rem; color: red"
              :value="LBChangeBoxes"
          />
        </div>

        <div class="table-row">
          <span>LC</span>
          <span style="margin-left: 3.5rem">{{ LCRollsAmount }}</span>
          <span style="margin-left: 2.75rem">{{ LCRollsBoxes() }}</span>
          <span style="margin-left: 7rem">{{ LCRemainingRolls }}</span>
          <a-input
              style="width: 7rem!important; margin-left: 10rem; color: red"
              :value="LCChangeBoxes"
          />
        </div>

        <!-- Sum -->
        <div class="table-row" style="border-top: 1px solid black; margin-top: 0.5rem; padding-top: 0.5rem">
          <span style="margin-left: 4.5rem">{{ RollsAmountSum }}</span>
          <span style="margin-left: 2.75rem">{{ RollsBoxesAmountSum }}</span>
          <span style="margin-left: 7rem">{{ RemainingRollsAmountSum }}</span>
          <span style="margin-left: 10rem; color: red">{{ ChangeBoxesAmountSum }}</span>
        </div>
      </div>

      <div style="display: flex; flex-direction: column; color: red; margin: 4.25rem 0 0 1rem">
        <span style="height: 2rem">{{ LA_ErrorMessage }}</span>
        <span style="height: 2rem">{{ LB_ErrorMessage }}</span>
        <span style="height: 2rem">{{ LC_ErrorMessage }}</span>
      </div>

      <div class="block" style="margin: 2rem 0 0.5rem 1rem; padding-top: 2rem">
        <div class="table-row" style="height: 2rem">
          <span>{{ LAMoreOrLessRolls }}</span>
          <span style="margin-left: 2rem">{{ Check_AKALA_and_AKBLA_Amount }}</span>
          <span style="margin-left: 2rem">{{ Check_AKALA_and_AKBLA_Chars }}</span>
        </div>

        <div class="table-row" style="height: 2rem">
          <span>{{ LBMoreOrLessRolls }}</span>
          <span style="margin-left: 2rem">{{ Check_AKALB_and_AKCLB_Amount }}</span>
          <span style="margin-left: 2rem">{{ Check_AKALB_and_AKCLB_Chars }}</span>
        </div>

        <div class="table-row" style="height: 2rem">
          <span>{{ LCMoreOrLessRolls }}</span>
          <span style="margin-left: 2rem">{{ Check_AKBLC_Amount }}</span>
          <span style="margin-left: 2rem">{{ Check_AKBLC_Chars }}</span>
        </div>
      </div>
    </div>

    <div style="display: flex; flex-direction: row">
      <div class="block" style="margin-top: 2rem">
        <span class="subtitle">
          Контейнеры:
        </span>

        <div class="basic-row">
          <span>С корпусами:</span>
          <span style="margin-left: 2rem">{{ calcContainersForCorps }}</span>
        </div>

        <div class="basic-row">
          <span>С лентой:</span>
          <span style="margin-left: 3.45rem">{{ calcContainersForRolls }}</span>
        </div>
      </div>

      <div style="display: flex; flex-direction: column; color: red; margin: 4.25rem 0 0 1rem">
        <span>{{ ContainersWithCorpsError }}</span>
        <span>{{ ContainersWithRollsError }}</span>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'CalculationTab',
  props: {
    // AKALA
    AKALAAmount: Number,
    AKALARollsAmount: Number,
    reCalcAKALARollsAmount: Function,
    // AKALB
    AKALBAmount: Number,
    AKALBRollsAmount: Number,
    reCalcAKALBRollsAmount: Function,
    // AKBLA
    AKBLAAmount: Number,
    AKBLARollsAmount: Number,
    reCalcAKBLARollsAmount: Function,
    // AKBLC
    AKBLCAmount: Number,
    AKBLCRollsAmount: Number,
    reCalcAKBLCRollsAmount: Function,
    // AKCLB
    AKCLBAmount: Number,
    AKCLBRollsAmount: Number,
    reCalcAKCLBRollsAmount: Function,
    // Sum
    audioCassettesSum: Number,
    rollsSum: Number,
    // Corps in one box
    inOneBoxCorps: Number,
    // Rolls in one box
    inOneBoxRolls: Number,
    // Round function
    round: Function,
    // Кратности
    AKALA: Number,
    AKALB: Number,
    AKBLA: Number,
    AKBLC: Number,
    AKCLB: Number,
    //
    inOneContainerBoxesCorps: Number,
    inOneContainerBoxesTape: Number,
    //
    updateKACorpsBoxes: Function,
    updateKBCorpsBoxes: Function,
    updateKCCorpsBoxes: Function,
    //
    updateLARollsBoxes: Function,
    updateLBRollsBoxes: Function,
    updateLCRollsBoxes: Function,
  },
  computed: {
    calcContainersForCorps() {
      return (this.CorpsBoxesSum / this.inOneContainerBoxesCorps).toFixed(3);
    },
    calcContainersForRolls() {
      return (this.RollsBoxesAmountSum / this.inOneContainerBoxesTape).toFixed(3);
    },
    // Corps Amount Calc
    KACorpsAmount() {
      return this.AKALAAmount + this.AKALBAmount;
    },
    KBCorpsAmount() {
      return this.AKBLAAmount + this.AKBLCAmount;
    },
    KCCorpsAmount() {
      return this.AKCLBAmount;
    },
    CorpsAmountSum() {
      return this.KACorpsAmount + this.KBCorpsAmount + this.KCCorpsAmount;
    },
    CorpsBoxesSum() {
      return this.KACorpsBoxes() + this.KBCorpsBoxes() + this.KCCorpsBoxes();
    },
    // Corps Boxes Sum Error Message
    CheckCorpsBoxesSum() {
      return this.isInt(this.KACorpsBoxes()) || this.isInt(this.KBCorpsBoxes()) || this.isInt(this.KCCorpsBoxes());
    },
    // Rolls Amount Calc
    LARollsAmount() {
      return Math.ceil(this.AKALARollsAmount + this.AKBLARollsAmount);
    },
    LBRollsAmount() {
      return Math.ceil(this.AKALBRollsAmount + this.AKCLBRollsAmount);
    },
    LCRollsAmount() {
      return Math.ceil(this.AKBLCRollsAmount);
    },
    // Rolls Boxes Amount Calc
    // LARollsBoxes() {
    //   return Math.ceil(this.LARollsAmount / this.inOneBoxRolls);
    // },
    // LBRollsBoxes() {
    //   return Math.ceil(this.LBRollsAmount / this.inOneBoxRolls);
    // },
    // LCRollsBoxes() {
    //   return Math.ceil(this.LCRollsAmount / this.inOneBoxRolls);
    // },
    // Remaining Rolls Amount Calc
    LARemainingRolls() {
      return this.round((this.LARollsBoxes() - (this.LARollsAmount / this.inOneBoxRolls)) * this.inOneBoxRolls);
    },
    LBRemainingRolls() {
      return this.round((this.LBRollsBoxes() - (this.LBRollsAmount / this.inOneBoxRolls)) * this.inOneBoxRolls);
    },
    LCRemainingRolls() {
      return this.round((this.LCRollsBoxes() - (this.LCRollsAmount / this.inOneBoxRolls)) * this.inOneBoxRolls);
    },
    RollsAmountSum() {
      return this.LARollsAmount + this.LBRollsAmount + this.LCRollsAmount;
    },
    RollsBoxesAmountSum() {
      return this.LARollsBoxes() + this.LBRollsBoxes() + this.LCRollsBoxes();
    },
    RemainingRollsAmountSum() {
      return this.LARemainingRolls + this.LBRemainingRolls + this.LCRemainingRolls;
    },
    ChangeBoxesAmountSum() {
      return this.LAChangeBoxes + this.LBChangeBoxes + this.LCChangeBoxes;
    },
    //
    LAMoreOrLessRolls() {
      return this.LARemainingRolls + this.LAChangeBoxes * this.inOneBoxRolls;
    },
    LBMoreOrLessRolls() {
      return this.LBRemainingRolls + this.LBChangeBoxes * this.inOneBoxRolls;
    },
    LCMoreOrLessRolls() {
      return this.LCRemainingRolls + this.LCChangeBoxes * this.inOneBoxRolls;
    },
    //
    Check_AKALA_and_AKBLA_Amount() {
      return this.AKBLAAmount < this.AKALAAmount ? this.AKALA : this.AKBLA;
    },
    Check_AKALA_and_AKBLA_Chars() {
      return this.AKBLAAmount < this.AKALAAmount ? 'KA' : 'KB';
    },
    Check_AKALB_and_AKCLB_Amount() {
      return this.AKCLBAmount < this.AKALBAmount ? this.AKALB : this.AKCLB;
    },
    Check_AKALB_and_AKCLB_Chars() {
      return this.AKCLBAmount < this.AKALBAmount ? 'KA' : 'KC';
    },
    Check_AKBLC_Amount() {
      return this.AKBLC;
    },
    Check_AKBLC_Chars() {
      return 'KB';
    },
    // Rolls Error messages
    LA_ErrorMessage() {
      const word = this.LAMoreOrLessRolls < 0 ? 'Лишние ' : 'Не хватает ';
      const amount = Math.abs(this.LAMoreOrLessRolls * this.Check_AKALA_and_AKBLA_Amount);
      const type = ' корпусов ' + this.Check_AKALA_and_AKBLA_Chars;
      return word + amount + type;
    },
    LB_ErrorMessage() {
      const word = this.LBMoreOrLessRolls < 0 ? 'Лишние ' : 'Не хватает ';
      const amount = Math.abs(this.LBMoreOrLessRolls * this.Check_AKALB_and_AKCLB_Amount);
      const type = ' корпусов ' + this.Check_AKALB_and_AKCLB_Chars;
      return word + amount + type;
    },
    LC_ErrorMessage() {
      const word = this.LCMoreOrLessRolls < 0 ? 'Лишние ' : 'Не хватает ';
      const amount = Math.abs(this.LCMoreOrLessRolls * this.Check_AKBLC_Amount);
      const type = ' корпусов ' + this.Check_AKBLC_Chars;
      return word + amount + type;
    },
    ContainersWithCorpsError() {
      return (this.calcContainersForCorps % 1) >= 0.5 ? 'Контейнер не заполнен' : 'Лишние коробки';
    },
    ContainersWithRollsError() {
      return (this.calcContainersForRolls % 1) >= 0.5 ? 'Контейнер не заполнен' : 'Лишние коробки';
    }
  },
  data() {
    return {
      LAChangeBoxes: -1,
      LBChangeBoxes: 0,
      LCChangeBoxes: 0,
    };
  },
  methods: {
    isInt(n) {
      return n % 1 === 0;
    },
    KACorpsBoxes() {
      const amount = this.KACorpsAmount / this.inOneBoxCorps;
      this.updateKACorpsBoxes(amount);
      return amount;
    },
    KBCorpsBoxes() {
      const amount = this.KBCorpsAmount / this.inOneBoxCorps;
      this.updateKBCorpsBoxes(amount);
      return amount;
    },
    KCCorpsBoxes() {
      const amount = this.KCCorpsAmount / this.inOneBoxCorps;
      this.updateKCCorpsBoxes(amount);
      return amount;
    },
    LARollsBoxes() {
      const amount = Math.ceil(this.LARollsAmount / this.inOneBoxRolls);
      this.updateLARollsBoxes(amount);
      return amount;
    },
    LBRollsBoxes() {
      const amount = Math.ceil(this.LBRollsAmount / this.inOneBoxRolls);
      this.updateLBRollsBoxes(amount);
      return amount;
    },
    LCRollsBoxes() {
      const amount = Math.ceil(this.LCRollsAmount / this.inOneBoxRolls);
      this.updateLCRollsBoxes(amount);
      return amount;
    }
  }
}
</script>

<style scoped lang="scss">
.calculation-tab {
  display: flex;
  justify-content: center;
  flex-direction: column;

  .block {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    border: 1px solid black;
    padding: 0.5rem;
    margin-bottom: 0.5rem;
    max-width: 40rem;

    .table-titles {
      display: flex;
      justify-content: space-between;
    }

    .table-row {
      display: flex;
      align-items: center;
    }
  }

  .subtitle {
    display: flex;
    justify-content: flex-start;
    margin-bottom: 0.5rem;
    font-weight: bold;
  }

  .basic-row {
    display: flex;
    justify-content: flex-start;
  }
}
</style>