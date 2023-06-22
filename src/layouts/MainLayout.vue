<template>
  <div class="q-container max-width">
    <div class="q-pa-md">
      <div class="q-gutter-md q-mb-md q-mt-lg">
        <div class="row">
          <div class="col">
            <q-input v-model="columnOne" label="Column One" />
          </div>
          <div class="col">
            <q-input v-model="columnTwo" label="Column Two" class="q-ml-md" />
          </div>
        </div>
        <div class="row justify-end">
          <div class="q-col-auto">
            <q-btn @click="saveData" label="Save" style="background-color:rgb(190, 247, 158)" />
          </div>
          <div class="q-col-auto">
            <q-btn @click="clearData" label="Cancel" class="q-ml-md" style="background-color: rgb(231, 231, 230);" />
          </div>
        </div>
      </div>
      <q-table :rows="tableData" :columns="columns" class="q-mt-lg" style="font-size: 10em;">
        <template v-slot:body-cell-action="{ row }">
          <q-td>
            <div class="text-center">
              <q-btn @click="deleteRow(row)" dense flat round icon="delete" color="negative" />
            </div>
          </q-td>
        </template>
      </q-table>
      <div class="q-mt-md row justify-end">
        <q-btn @click="redirectToOtherPage" label="Close" style="background-color: rgb(231, 231, 230);" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      columnOne: '',
      columnTwo: '',
      tableData: [],
      columns: [
        {
          name: 'columnOne',
          label: 'Column One',
          field: 'columnOne',
          sortable: true,
          align: 'center'
        },
        {
          name: 'columnTwo',
          label: 'Column Two',
          field: 'columnTwo',
          sortable: true,
          align: 'center'
        },
        {
          name: 'action',
          required: true,
          label: 'Action',
          align: 'center'
        }
      ]
    };
  },
  methods: {
    saveData() {
      if (this.columnOne && this.columnTwo) {
        this.tableData.push({ columnOne: this.columnOne, columnTwo: this.columnTwo });
        this.columnOne = '';
        this.columnTwo = '';
      }
    },
    clearData() {
      this.columnOne = '';
      this.columnTwo = '';
    },
    deleteRow(row) {
      const index = this.tableData.indexOf(row);
      if (index > -1) {
        this.tableData.splice(index, 1);
      }
    },
    redirectToOtherPage() {
      // Replace 'other-page-url' with the URL of the other page you want to redirect to
      window.location.href = 'other-page-url';
    }
  }
};
</script>

<style scoped>
.max-width {
  max-width: 80%;
  margin: 0 auto;
}
.q-mt-lg {
  margin-top: 100px;
}
.text-center {
  text-align: center;
}
</style>
