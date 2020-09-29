<template>
  <div id="app">
    <div>
      <button @click="unshift">array.unshift</button>
      <button @click="shift">array.shift</button>
      <button @click="push">array.push</button>
      <button @click="pop">array.pop</button>
    </div>
    <div>
      <span>array.filter</span>
      <select v-model="selectedTeam">
        <option v-for="team in teams" :key="team" :value="team">
          {{ team }}
        </option>
      </select>
    </div>
    <div>
      <table>
        <thead>
          <th></th>
          <th>
            <input type="checkbox" v-model="allChecked" @click="map" />
          </th>
          <th>id</th>
          <th>name</th>
          <th>team</th>
        </thead>
        <tbody>
          <tr v-for="(row, index) in filterdRows" :key="row.id">
            <td>
              {{ index }}
            </td>
            <td>
              <input type="checkbox" v-model="row.checked" @click="every" />
            </td>
            <td>
              {{ row.id }}
            </td>
            <td>
              {{ row.name }}
            </td>
            <td>
              {{ row.team }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {},
  data() {
    return {
      allChecked: false,
      selectedTeam: '',
      teams: [
        '',
        'business',
        'new function',
        'infra',
        'design',
        'qa'
      ],
      rows: [
        { id: 1 , name: 'kohei.yoshida', team: 'business', checked: false },
        { id: 2 , name: 'toshiaki.doi', team: 'new function', checked: false },
        { id: 3 , name: 'kazutaka.hamada', team: 'new function', checked: false },
        { id: 4 , name: 'hirotake.ikeda', team: 'infra', checked: false },
        { id: 5 , name: 'kazuho.inoue', team: 'new function', checked: false },
        { id: 6 , name: 'shuntaro.kishi', team: 'new function', checked: false },
        { id: 7 , name: 'mai.kawaoka', team: 'design', checked: false },
        { id: 8 , name: 'miho.hiroshima', team: 'new function', checked: false },
        { id: 9 , name: 'haruhi.misono', team: 'new function', checked: false },
        { id: 10 , name: 'ken.miyauchi', team: 'qa', checked: false },
        { id: 11 , name: 'mayu.morimoto', team: 'new function', checked: false },
        { id: 12 , name: 'nao.ueno', team: 'qa', checked: false },
        { id: 13 , name: 'souichiro.houri', team: 'design', checked: false },
        { id: 14 , name: 'yamato.takezaki', team: 'design', checked: false },
        { id: 15 , name: 'miku.wakabayashi', team: 'new function', checked: false },
        { id: 16 , name: 'hiro.yagi', team: 'infra', checked: false },
        { id: 17 , name: 'ryuya.matsunawa', team: 'new function', checked: false },
      ]
    }
  },
  computed: {
    filterdRows: function () {
      if( this.selectedTeam == '' ) return this.rows;
      return this.rows.filter(
        row => row.team == this.selectedTeam
      );
    } 
  },
  methods: {

    /**
     * 要素を先頭に追加する
     */
    unshift() {
      this.rows.unshift(
        { 
          id: this.rows.length ,
          name: 'member' + this.rows.length,
          team: 'seattle',
          checked: false
        }
      );
    },

    /**
     * 要素を先頭に取り出す
     */
    shift() {
      this.rows.shift();
    },

    /**
     * 要素を末尾に追加する
     */
    push() {
      this.rows.push(
        { 
          id: this.rows.length ,
          name: 'member' + this.rows.length,
          team: 'seattle',
          checked: false
        }
      );
    },

    /**
     * 要素を末尾から取り出す
     */
    pop() {
      this.rows.pop();
    },

    /**
     * andをとる
     */
    every() {
      this.allChecked = this.rows.every(row => row.checked);
    },

    /**
     * 一括で変更する
     */
    map() {
      this.rows.map(row => row.checked = this.allChecked);
    }
    

  }
}
</script>

<style>
  div {
    padding: 5px;
  }
  table {
    table-layout: fixed;
    border-collapse: collapse;
  }
  th, td {
    text-align: center;
    border: solid 1px #cbcbcb;
    padding: 5px;
    width: 150px;
  }
  select {
    margin: 10px;
  }
  button {
    margin: 10px;
  }
</style>
