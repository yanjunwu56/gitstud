<template>
  <div>
      <el-table :data="users" highlight-current-row v-loading="listLoading" @selection-change="selsChange" style="width: 100%;">
			<el-table-column type="selection" width="55">
			</el-table-column>
			<el-table-column type="index" width="60">
			</el-table-column>
			<el-table-column prop="name" label="商品名称" width="120" sortable>
			</el-table-column>
			<el-table-column prop="price" label="价格" width="100" sortable>
			</el-table-column>
			<el-table-column prop="reserve" label="商品库存" min-width="120" sortable>
			</el-table-column>
			<el-table-column prop="desc" label="商品描述" min-width="180" sortable>
			</el-table-column>
			<el-table-column label="操作" width="150">
				<template scope="scope">
					<el-button size="small" @click="handleEdit(scope.$index, scope.row)">编辑<span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;">     </span></el-button>
				</template>
			</el-table-column>
</el-table>

<!--编辑界面-->
		<el-dialog title="编辑" v-model="editFormVisible" :close-on-click-modal="false">
			<el-form :model="editForm" label-width="80px" :rules="editFormRules" ref="editForm">
				<el-form-item label="商品名称" prop="name">
					<el-input v-model="editForm.name" auto-complete="off"></el-input>
				</el-form-item>
				<el-form-item label="商品价格">
					<el-input-number v-model="editForm.price"></el-input-number>
				</el-form-item>
				<el-form-item label="商品库存">
					<el-input-number v-model="editForm.reserve"></el-input-number>
				</el-form-item>
				<el-form-item label="商品描述">
					<el-input type="textarea" v-model="editForm.desc"></el-input>
				</el-form-item>
			</el-form>
			<div slot="footer" class="dialog-footer">
				<el-button @click.native="editFormVisible = false">取消</el-button>
				<el-button type="primary" @click.native="editSubmit" :loading="editLoading">提交<span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span><span class="space" style="white-space:pre;display:inline-block;text-indent:2em;line-height:inherit;"> </span></el-button>
			</div>
		</el-dialog>
  </div>
</template>
<script src="https://unpkg.com/element-ui/lib/index.js"></script>
<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
     
// 编辑界面数据
				editForm: {
					id: 0,
					name: '',
					price: 0,
					desc: '',
					reserve:'',
                },
                
    }
  },
  methods:{
      //显示编辑界面  
            handleEdit: function (index, row) {  
                this.editFormVisible = true;  
                <span style="color:#ff0000;">this.editForm = Object.assign({}, row);</span>  
            }   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

 @import "https://unpkg.com/element-ui/lib/theme-chalk/index.css";

</style>
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
