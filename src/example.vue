<template>
  <div>
    <ul v-if="posts && posts.length">
      <li v-for="(index, post) of posts" :key="index">
        <p><strong>{{ post.title }}</strong></p>
        <p>{{ post.body }}</p>
      </li>
    </ul>

    <ul v-if="errors && errors.length">
      <li v-for="(index, error) of errors" :key="index">
        {{ error.message }}
      </li>
    </ul>
  </div>
</template>

<script>
import Axios from 'axios';

export default {
  data () => ({
    posts: [],
    errors: [],
  }),

// Создаем запрос, когда компонент будет создан
created () {
  axios.get('https://jsonplaceholder.typicode.com/posts')
  .then(response => {
// JSON ответ будет автоматически распарсен
this.posts = response.data
  })
.cashe(e => {
  this.errors.push(e)
})
}
}
</script>