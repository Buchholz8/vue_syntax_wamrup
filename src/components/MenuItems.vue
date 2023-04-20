<template>
  <div>
    <section>
      <input type="number" ref="item_filter" />
      <button @click="price_filter">Price Filter</button>
    </section>
    <section v-for="(item, i) in items" :key="i">
      <div v-if="item.price <= max_price">
        <p>{{ item.title }}</p>
        <p>{{ item.description }}</p>
        <img :src="item.image_url" alt="picture of items" />
        <p>${{ item.price }}</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  methods: {
    price_filter: function () {
      let user_input = this.$refs[`item_filter`];
      let input_value = user_input[`value`];
      this.max_price = input_value;
    },
  },
  data() {
    return {
      max_price: 100,
      items: [
        {
          title: `egg`,
          price: 1,
          description: `we sell eggs`,
          image_url: `https://images.pexels.com/photos/6625253/pexels-photo-6625253.jpeg?auto=compress&cs=tinysrgb&w=400`,
        },
        {
          title: `bacon`,
          price: 12,
          description: `we sell bacon`,
          image_url: `https://images.pexels.com/photos/1927377/pexels-photo-1927377.jpeg?auto=compress&cs=tinysrgb&w=400`,
        },
        {
          title: `cheese`,
          price: 6,
          description: `we sell cheese`,
          image_url: `https://images.pexels.com/photos/773253/pexels-photo-773253.jpeg?auto=compress&cs=tinysrgb&w=400`,
        },
        {
          title: `milk`,
          price: 4,
          description: `we sell milk`,
          image_url: `https://images.pexels.com/photos/248412/pexels-photo-248412.jpeg?auto=compress&cs=tinysrgb&w=400`,
        },
      ],
    };
  },
};
</script>

<style scoped>
img {
  width: 80px;
  height: 80px;
}
</style>