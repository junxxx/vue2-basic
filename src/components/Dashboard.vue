<script setup>
</script>

<template>
  <div>
    <el-button type="text" @click="dialogFormVisible = true">New</el-button>
    <el-dialog title="Shipping address" :visible.sync="dialogFormVisible">
      <el-form :model="form">
        <el-form-item label="Date">
          <el-date-picker
            v-model="form.date"
            type="date"
            placeholder="Pick a day">
          </el-date-picker>
        </el-form-item>
        <el-form-item label="Name" >
          <el-input v-model="form.name" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="State" >
          <el-input v-model="form.state" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="City" >
          <el-input v-model="form.city" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Address" >
          <el-input v-model="form.address" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="Zip" >
          <el-input v-model="form.zip" autocomplete="off"></el-input>
        </el-form-item>
      </el-form>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">Cancel</el-button>
        <el-button type="primary" @click="addItem">Confirm</el-button>
      </span>
    </el-dialog>
    <div>
      <el-table
        :data="tableData"
        style="width: 100%">
        <el-table-column
          fixed
          prop="date"
          label="Date"
          width="150">
        </el-table-column>
        <el-table-column
          prop="name"
          label="Name"
          width="120">
        </el-table-column>
        <el-table-column
          prop="state"
          label="State"
          width="120">
        </el-table-column>
        <el-table-column
          prop="city"
          label="City"
          width="120">
        </el-table-column>
        <el-table-column
          prop="address"
          label="Address"
          width="300">
        </el-table-column>
        <el-table-column
          prop="zip"
          label="Zip"
          width="120">
        </el-table-column>
        <el-table-column
          fixed="right"
          label="Operations"
          width="120">
          <template slot-scope="scope">
            <el-button @click="handleClick" type="text" size="small">Detail</el-button>
            <el-button type="text" size="small">Edit</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
  export default {
    methods: {
      handleClick() {
        console.log('click');
      },
      addItem() {
        const {date, name, state, city, address, zip} = this.form;
        const item = {
          date: date.toISOString().split('T')[0],
          name, state, city, address, zip
        };

        // add a new itme to table data
        this.tableData.push(item);
        // close dialog
        this.dialogFormVisible = false;
      },
    },
    data() {
      return {
        tableData: [],
        dialogFormVisible: false,
        form: {
          date: '',
          name: '',
          state: '',
          city: '',
          address: '',
          zip: '',
        }
      }
    }
  }
</script>
