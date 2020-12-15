<template>
  <div class="table-wrapper" style="margin-top: 1rem">
    <div class="header">
      <div class="saldo">
        <div class="saldo-item">
          <span style="color: blue">Сальдо до начала периода RUR</span>
          <span style="background-color: #efff74; margin-left: 1rem">1,00</span>
        </div>
        <div class="saldo-item">
          <span style="color: blue">Сальдо до начала периода USD</span>
          <span style="background-color: #efff74; margin-left: 1rem">1,00</span>
        </div>
        <div class="saldo-item">
          <span style="color: blue">Сальдо до начала периода EUR</span>
          <span style="background-color: #efff74; margin-left: 1rem">1,00</span>
        </div>
      </div>

      <div class="buttons">
        <div style="margin-bottom: 0.5rem">
          <a-button style="width: 15rem">Курс</a-button>
          <a-button style="width: 15rem; margin: 0 0.5rem">Расчёт налогов</a-button>
          <a-button style="width: 15rem">Замена формул</a-button>
        </div>
        <a-button style="width: 46rem">Полный расчёт ТовДенПотоки</a-button>
      </div>

      <div class="money-button" style="display: flex; flex-direction: column; margin-left: 1rem">
        <a-button size="small" style="color: red">RUR</a-button>
        <a-button size="small" style="color: red">USD</a-button>
        <a-button size="small" style="color: red">EUR</a-button>
      </div>
    </div>

    <div class="oborots" style="margin-top: 1rem">
      <span style="margin-left: 37rem; margin-right: 2rem">ОБОРОТЫ</span>
      <span style="margin-right: 4rem">7 494 205,60</span>
      <span>7 519 011,65</span>
    </div>

    <a-table
        :columns="columns"
        :data-source="data"
        bordered
        size="middle"
        :pagination="{total: 50}"
    />
  </div>
</template>

<script>
const columns = [
  {
    title: 'Наименование операции и срок  её проведения',
    children: [
      {
        title: 'Наименование операции',
        dataIndex: 'name',
        key: 'name',
        width: 200,
        sorter: (a, b) => a.age - b.age,
      },
      {
        title: 'Дата',
        dataIndex: 'date',
        key: 'date',
        width: 100,
        sorter: (a, b) => a.age - b.age,
      },
    ]
  },
  {
    title: 'Признак',
    children: [
      {
        title: 'НДС',
        dataIndex: 'nds',
        key: 'nds',
        width: 75,
        sorter: (a, b) => a.age - b.age,
      },
      {
        title: 'Налог с оборотов',
        dataIndex: 'turnoverTax',
        key: 'turnoverTax',
        width: 75,
        sorter: (a, b) => a.age - b.age,
      },
      {
        title: 'Налог на прибыль',
        dataIndex: 'incomeTax',
        key: 'incomeTax',
        width: 75,
        sorter: (a, b) => a.age - b.age,
      },
      {
        title: 'Деньги',
        dataIndex: 'money',
        key: 'money',
        width: 75,
        sorter: (a, b) => a.age - b.age,
      },
    ]
  },
  {
    title: 'Эквивалент денежных средств по курсу',
    children: [
      {
        title: 'Поступление',
        dataIndex: 'income',
        key: 'income',
        width: 100,
        sorter: (a, b) => a.age - b.age,
      },
      {
        title: 'Списано',
        dataIndex: 'outcome',
        key: 'outcome',
        width: 100,
        sorter: (a, b) => a.age - b.age,
      },
    ]
  },
  {
    title: 'Валюта',
    children: [
      {
        title: 'Валюта',
        dataIndex: 'currency',
        key: 'currency',
        width: 75,
        sorter: (a, b) => a.age - b.age,
      },
      {
        title: 'Курс',
        dataIndex: 'course',
        key: 'course',
        width: 75,
        sorter: (a, b) => a.age - b.age,
      },
    ]
  },
];

const data = [
  {
    key: 1,
    name: 'Приобритение товара',
    date: '05.01.02',
    nds: '1',
    turnoverTax: '',
    incomeTax: '1',
    money: '',
    income: '',
    outcome: '1 080 000,00',
    currency: 'RUR',
    course: '1,00',
  },
  {
    key: 2,
    name: 'Оплата приобритенного товара',
    date: '06.01.02',
    nds: '',
    turnoverTax: '',
    incomeTax: '',
    money: '1',
    income: '',
    outcome: '1 080 000,00',
    currency: 'RUR',
    course: '1,00',
  },
  {
    key: 3,
    name: 'Оплата услуг экспедиторов',
    date: '11.01.02',
    nds: '',
    turnoverTax: '',
    incomeTax: '',
    money: '1',
    income: '',
    outcome: '120 000,00',
    currency: 'RUR',
    course: '1,00',
  },
  {
    key: 4,
    name: 'Таможенные расходы',
    date: '14.01.02',
    nds: '',
    turnoverTax: '',
    incomeTax: '1',
    money: '1',
    income: '',
    outcome: '6 000,00',
    currency: 'RUR',
    course: '1,00',
  },
  {
    key: 5,
    name: 'Услуги экспедирования',
    date: '15.01.02',
    nds: '1',
    turnoverTax: '',
    incomeTax: '1',
    money: '',
    income: '',
    outcome: '120 000,00',
    currency: 'RUR',
    course: '1,00',
  },
  {
    key: 6,
    name: 'Реализация товара',
    date: '16.01.02',
    nds: '',
    turnoverTax: '1',
    incomeTax: '1',
    money: '',
    income: '1 200 000,00',
    outcome: '',
    currency: 'USD',
    course: '10,00',
  },
  {
    key: 7,
    name: 'Поступление денег от покупателя',
    date: '16.02.02',
    nds: '',
    turnoverTax: '',
    incomeTax: '',
    money: '1',
    income: '1 200 000,00',
    outcome: '',
    currency: 'USD',
    course: '10,00',
  },
  {
    key: 8,
    name: 'Оплата услуг по конвертации',
    date: '16.02.02',
    nds: '',
    turnoverTax: '',
    incomeTax: '1',
    money: '1',
    income: '6 000,00',
    outcome: '',
    currency: 'RUR',
    course: '1,00',
  },
  {
    key: 9,
    name: 'Конвертация',
    date: '17.02.02',
    nds: '',
    turnoverTax: '',
    incomeTax: '',
    money: '1',
    income: '-1 200 000,00',
    outcome: '',
    currency: 'USD',
    course: '10,00',
  },
];

export default {
  name: 'MoneyComponent',
  data() {
    return {
      data,
      columns,
    };
  },
}
</script>

<style scoped lang="scss">
.table-wrapper {
  margin: 0 2rem;
  color: black;

  .header {
    display: flex;
    justify-content: space-between;
  }

  .oborots {
    font-size: 1.15rem;
  }

  .saldo {
    font-size: 1.115rem;
    margin-right: 1rem;
  }
}
</style>