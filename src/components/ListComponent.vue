<template>
  <div class="row m-3">
    <div class="col-md-6">
      <h2>產品列表</h2>
      <table class="table table-hover">
        <thead>
          <tr>
            <th>產品名稱</th>
            <th>原價</th>
            <th>售價</th>
            <th>是否啟用</th>
            <th>查看細節</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in products" :key="product.id">
            <td>{{ product.title }}</td>
            <td>{{ product.origin_price }}</td>
            <td>{{ product.price }}</td>
            <td>
              <span v-if="product.is_enabled" class="text-success">啟用</span>
              <span v-else>未啟用</span>
            </td>
            <td>
              <button type="button" class="btn btn-primary" @click="tempProduct = product">
                查看細節
              </button>
            </td>
          </tr>
        </tbody>
        <tfoot>
          <tr colspan="5">
            目前有{{products.length}} 項產品
          </tr>
        </tfoot>
      </table>
    </div>
    <div class="col-md-6">
      <h2>單一產品細節</h2>
      <p v-if="!tempProduct.title" class="text-secondary">請選擇一個商品查看</p>
       <div v-else>
        <div class="card mb-3">
          <img :src="tempProduct.imageUrl" class="card-img-top primary-image" alt="產品圖" />
          <div class="card-body">
            <h5 class="card-title">
              {{ tempProduct.title }}
              <span class="badge bg-primary ms-2">{{ tempProduct.category }}</span>
            </h5>
            <p class="card-text">商品描述：{{ tempProduct.description }}</p>
            <p class="card-text">商品內容：{{ tempProduct.content }}</p>
            <p class="card-text">
              {{ tempProduct.price }} <del>{{ tempProduct.origin_price }}</del
              >{{ tempProduct.unit }}/個
            </p>
          </div>
        </div>

        <span v-for="(image, id) in tempProduct.imagesUrl" :key="id" class="me-2">
          <img :src="image" alt="" class="images" />
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        {
          category: '甜甜圈',
          content: '尺寸：14x14cm',
          description: '濃郁的草莓風味，中心填入滑順不膩口的卡士達內餡，帶來滿滿幸福感！',
          id: '-L9tH8jxVb2Ka_DYPwng',
          is_enabled: 1,
          origin_price: 150,
          price: 99,
          title: '草莓莓果夾心圈',
          unit: '元',
          num: 10,
          imageUrl:
            'https://images.unsplash.com/photo-1583182332473-b31ba08929c8?ixid=MnwxMjA3fDB8MHxzZWFyY2h8NzR8fGRvbnV0fGVufDB8fDB8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60',
          imagesUrl: [
            'https://images.unsplash.com/photo-1626094309830-abbb0c99da4a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2832&q=80',
            'https://images.unsplash.com/photo-1559656914-a30970c1affd?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTY0fHxkb251dHxlbnwwfHwwfHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60'
          ]
        },
        {
          category: '蛋糕',
          content: '尺寸：6寸',
          description: '蜜蜂蜜蛋糕，夾層夾上酸酸甜甜的檸檬餡，清爽可口的滋味讓人口水直流！',
          id: '-McJ-VvcwfN1_Ye_NtVA',
          is_enabled: 16,
          origin_price: 1000,
          price: 900,
          title: '蜂蜜檸檬蛋糕',
          unit: '元',
          num: 1,
          imageUrl:
            'https://images.unsplash.com/photo-1627834377411-8da5f4f09de8?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1001&q=80',
          imagesUrl: [
            'https://images.unsplash.com/photo-1618888007540-2bdead974bbb?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=987&q=80'
          ]
        },
        {
          category: '蛋糕',
          content: '尺寸：6寸',
          description: '法式煎薄餅加上濃郁可可醬，呈現經典的美味及口感。',
          id: '-McJ-VyqaFlLzUMmpPpm',
          is_enabled: 1,
          origin_price: 700,
          price: 600,
          title: '暗黑千層',
          unit: '元',
          num: 15,
          imageUrl:
            'https://images.unsplash.com/photo-1505253149613-112d21d9f6a9?ixid=MnwxMjA3fDB8MHxzZWFyY2h8NDZ8fGNha2V8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60',
          imagesUrl: [
            'https://images.unsplash.com/flagged/photo-1557234985-425e10c9d7f1?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTA5fHxjYWtlfGVufDB8fDB8fA%3D%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60',
            'https://images.unsplash.com/photo-1540337706094-da10342c93d8?ixid=MnwxMjA3fDB8MHxzZWFyY2h8NDR8fGNha2V8ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=700&q=60'
          ]
        }
      ],
      tempProduct: {}
    }
  },
}
</script>
