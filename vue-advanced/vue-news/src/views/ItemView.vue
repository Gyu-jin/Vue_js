<template>
  <div>
    <section>
      <!-- 질문 상세정보 -->
      <div class="user-containar">
        <div>
          <!-- 사용자 프로필 -->
          <i class="fas fa-user"></i>
        </div>
        <div class="user-description">
          <!-- 사용자 정보 -->
          <router-link :to="`/user/${fetchedItem.user}`">
            {{ fetchedItem.user }}
          </router-link>
          <div class="time">
            {{ fetchedItem.time_ago }}
          </div>
        </div>
      </div>
      <h2>{{ fetchedItem.title }}</h2>
    </section>
    <section>
      <!-- 질문 댓글 -->
      <!-- v-html  => html 테그를 그대로 표현해준다. -->
      <div v-html="fetchedItem.content">
        <!-- {{ fetchedItem.content }} -->
      </div>
    </section>
      <!-- {{ this.$store.state.item }}
      <p>{{ fetchedItem.title }}</p>
      
      <div>
        {{ fetchedItem.content }}
      </div> -->
  </div>
</template>

<script>
import { mapGetters} from 'vuex'

export default {
  computed: {
      ...mapGetters(['fetchedItem']),
  },
  created(){
    const itemId = this.$route.params.id;
    this.$store.dispatch('FETCH_ITEM',itemId);
  }
}
</script>

<style scoped>

.user-containar{
  display: flex;
  align-items: center;
  padding: 0.5rem;
}
.fa-user{
  font-size: 2.5rem;
}
.user-description{
  padding-left: 8px;
}
.time{
  font-size: 0.7rem;
}

</style>