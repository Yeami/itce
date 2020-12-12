<template>
  <div class="multiplicity-tab">

    <div class="block">
      <span class="subtitle">
        Корпуса
      </span>

      <div class="basic-row">
        <span>В одном контейнере (коробок):</span>
        <a-input :value="inOneContainerBoxesCorps"/>
      </div>

      <div class="basic-row">
        <span>В одной коробке корпусов (шт):</span>
        <a-input :value="inOneBoxCorps"/>
      </div>
    </div>


    <div class="block">
      <span class="subtitle">
        Лента
      </span>

      <div class="basic-row">
        <span>В одном контейнере (коробок):</span>
        <a-input :value="inOneContainerBoxesTape"/>
      </div>

      <div class="basic-row">
        <span>В одной коробке (рулонов):</span>
        <a-input :value="inOneBoxRolls"/>
      </div>
    </div>


    <div class="block">
      <span class="subtitle">
        Аудиокассеты
      </span>

      <div class="basic-row">
        <span>AKALA:</span>
        <a-input :value="AKALA"/>
      </div>

      <div class="basic-row">
        <span>AKALB:</span>
        <a-input :value="AKALB"/>
      </div>

      <div class="basic-row">
        <span>AKBLA:</span>
        <a-input :value="AKBLA"/>
      </div>

      <div class="basic-row">
        <span>AKBLC:</span>
        <a-input :value="AKBLC"/>
      </div>

      <div class="basic-row">
        <span>AKCLB:</span>
        <a-input :value="AKCLB"/>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'MultiplicityTab',
  props: {
    inOneContainerBoxesCorps: Number,
    inOneBoxCorps: Number,
    inOneContainerBoxesTape: Number,
    inOneBoxRolls: Number,
    AKALA: Number,
    AKALB: Number,
    AKBLA: Number,
    AKBLC: Number,
    AKCLB: Number,
  }
}
</script>

<style scoped lang="scss">
.multiplicity-tab {
  display: flex;
  justify-content: center;
  flex-direction: column;
  width: 36.25rem;

  .block {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    align-items: flex-start;
    border: 1px solid black;
    padding: 0.5rem;
    margin-bottom: 0.5rem;
  }

  .subtitle {
    font-size: 1.25rem;
    margin-bottom: 0.5rem;
  }

  .basic-row {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-bottom: 0.5rem;

    span {
      width: 22.5rem;
      text-align: left;
    }
  }
}
</style>