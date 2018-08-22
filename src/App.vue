<template lang="html">
  <div class="card">

    <div class="card-header bg-info text-white">

      <h4 class="text-center mb-2">Employee Probation/Evaluation Dates</h4>

      <div v-if="true" class="form-group m-0 d-flex">
        <div class="input-group input-group-sm">
          <div class="input-group-prepend">
            <span class="input-group-text">Hire Date:</span>
          </div>
          <input type="date" v-model="hireDate" class="form-control">
        </div>
      </div>

      <div v-else class="form-group m-0 d-flex">
        <select class="form-control form-control-sm" v-model="hireMonth">
          <option :value="null" selected disabled>Hire Month</option>
          <option v-for="(month, index) in months" :value="index">{{ month }}</option>
        </select>
        <input type="number" v-model="hireDay" class="form-control form-control-sm" placeholder="Hire Day">
        <input type="number" v-model="hireYear" class="form-control form-control-sm" placeholder="Hire Year">
      </div>
    </div>

    <table class="table table-striped table-bordered m-0">
      <tbody>
        <tr>
          <th>Pre Planning Due Date:</th>
          <td class="text-center">{{ hireMoment.format('LL') }}</td>
        </tr>
        <tr>
          <th>Midterm Due Date:</th>
          <td class="text-center">{{ midTerm.format('LL') }}</td>
        </tr>
        <tr>
          <th>End of Term Due Date:</th>
          <td class="text-center">{{ endTerm.format('LL') }}</td>
        </tr>
        <tr>
          <th>Evaluation Cycle Begin Date:</th>
          <td class="text-center">{{ hireMoment.format('LL') }}</td>
        </tr>
        <tr>
          <th>Evaluation Cycyle End Date:</th>
          <td class="text-center">{{ endTerm.format('LL') }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  props: {
    midTermVal: {
      type: Number,
      default: 3
    },
    midTermUnit: {
      type: String,
      default: 'months'
    },
    endTermVal: {
      type: Number,
      default: 6
    },
    endTermUnit: {
      type: String,
      default: 'months'
    }
  },
  data () {
    return {
      hireDate: null,
      hireMonth: null,
      hireDay: null,
      hireYear: null
    }
  },
  computed: {
    months () {
      return moment()._locale._months
    },
    hireMoment () {
      return moment(this.hireDate, 'YYYY-MM-DD')
    },
    midTerm () {
      return moment(this.hireMoment).add(this.midTermVal, this.midTermUnit)
    },
    endTerm () {
      return moment(this.hireMoment).add(this.endTermVal, this.endTermUnit)
    }
  },
  mounted () {
    this.hireDate = moment().format('YYYY-MM-DD')
  }
}
</script>
