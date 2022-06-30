<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model="age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="btn">添加/修改</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0" v-if="arr.length">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="item in arr" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>

          <td>
            <button @click="del(item.id)">删除</button>
            <button>编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: '',
      age: 0,
      sex: '',
      arr: []
    }
  },
  methods: {
    btn() {
      if (this.name.trim() === '' || this.age === 0 || this.sex == '') {
        return alert('请输入')
      }
      this.arr.push({
        id: this.arr[this.arr.length - 1] ? this.arr[this.arr.length - 1].id + 1 : 1,
        name: this.name,
        age: this.age,
        sex: this.sex
      })
    },
    del(id) {
      const index = this.arr.findIndex(ele => id == ele.id)
      console.log(index);
      this.arr.splice(index, 1)
    },
  }
}
</script>
