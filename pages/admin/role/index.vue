<template>
  <div>
    <a-layout-content
      :style="{ margin: '24px 16px', padding: '24px', background: '#fff', minHeight: '100vh' }"
    >
      <a-button class="create-button" @click="createRole" type="primary"><a-icon type="plus" /> CREATE</a-button>

      <a-table class="pt-4 admin-table" :columns="columns" :data-source="data" :loading="loading" bordered :row-key="record => record.id">
        <span class="table_item" slot="createdat" slot-scope="text, record">
          <span v-if="record.createdat != null"> {{ changeStringToTime(record.createdat) }} </span>
        </span>

        <span class="table_item" slot="updatedat" slot-scope="text, record">
          <span v-if="record.createdat != null"> {{ changeStringToTime(record.updatedat) }} </span>
        </span>

        <span class="table_item" slot="permission" slot-scope="text, record">
          <a-button class="btn_per"  type="primary" @click="getPermission(record)">
            <a-icon type="eye" /> <span class="item_title"> Permission</span>
          </a-button>
        </span>
      </a-table>

      <div>
        <a-modal width="450px" v-model="modalVisible" title="Permission">
          <template slot="footer">
            <a-button key="back" @click="handleCancelModal">
              Back
            </a-button>
            <a-button key="submit" type="primary" @click="editUser">
              Edit
            </a-button>
          </template>

          <a-tree :tree-data="treeData" show-icon default-expand-all>
            <i style="color: #017B01" slot="permission" class="fas fa-check"></i>
            <a-icon slot="key" type="key" />
            <a-icon slot="switcherIcon" type="down" />
          </a-tree>
        </a-modal>
      </div>
    </a-layout-content>
  </div>
</template>

<script src="./script.js"></script>

<style lang="scss" scoped>
@import url("./style.scss");
.create-button {
  background-color: #6B5B95;
  border-color: #6B5B95;
  width: 200px;
  height: 40px;
}
.btn_per {
  display: flex;
}
.anticon-eye{
  line-height:28px;
}
.table_item{
  display:flex;
  justify-content:center;
}
.item_title{
  line-height:31px;
}
</style>