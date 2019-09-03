<template>
  <div class="base">
    <p>
      <img class="logo" src="../images/logo.jpg" alt="ロゴ">
      <span class="sample">チャット</span>
    </p>
  <div class="chat">
    <li v-for="(row,index) in list" :key="index">
      <div class="balloon1">
        <p class="name">{{ row.name }}</p>
        <p class="text"> {{ row.message }}</p>
      </div>
    </li>
  </div>

  <form @submit="onSubmit">
    <div class="input">
      name<input v-model="$data.name" type="text">
      massage<textarea v-model="$data.text" type="text"></textarea>
      <button type="submit">送信</button>
    </div>
  </form>
  </div>
</template>

<script>
import socket from './utils/socket';

// components
import MyComponent from './components/MyComponent.vue';

export default {
  components: {
    MyComponent
  },
  data() {
    return {
      message: '',
      text: '',
      name,
      list: [],
    };
  },
  created() {
    socket.on('connect', () => {
      console.log('connected!');
    });

    socket.on('get_message', (message) => {
      console.log(message);
      this.list.push(message);
    });
  },
  methods: {
    /**
     * Enterボタンを押したとき
     */
    onSubmit(e) {
      e.preventDefault();
      socket.emit('post_message', {
        name: this.name,
        message: this.text
      });
      this.message = '';
    },
  }
};
</script>

<style lang="scss" scoped>
.logo {
  width: 40px;
}

.sample {
  color: $red;
}

.input {
  position: relative;
  display: block;
  background-color: #e0ffff;
  margin-left: auto;
  margin-right: auto;
}

li {
  font: 15px/24px sans-serif;
  list-style: none;
}

.input input[type='text'] {
  display: block;
  font: 15px/24px sans-serif;
}

textarea {
  display: block;
  font: 15px/24px sans-serif;
}

.balloon1 {
  position: relative;
  display: inline-block;
  margin: 1em 0;
  padding: 7px 10px;
  min-width: 120px;
  max-width: 100%;
  color: #555;
  font-size: 16px;
  background: #e0edff;
  border-radius: 15px;
}

.balloon1::before {
  position: absolute;
  top: 50%;
  right: -24px;
  margin-top: -12px;
  border: 12px solid transparent;
  border-left: 12px solid #fff;
  z-index: 2;
}

.balloon::after {
  position: absolute;
  top: 50%;
  right: -30px;
  margin-top: -14px;
  border: 14px solid transparent;
  border-left: 14px solid #555;
  z-index: 1;
}

.balloon1 p {
  margin: 0;
  padding: 0;
}

.name {
  color: #008080;
  font-size: 0.9em;
}

.text {
  color: #000080;
  font-size: 1.2em;
  word-wrap: break-word;
  white-space: normal;
}

</style>
