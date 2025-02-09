<script>
import { createClient } from '@supabase/supabase-js';
import CommentForm from './components/CommentForm.vue';

const supabaseUrl = 'https://your-supabase-url.supabase.co';
const supabaseKey = 'your-supabase-key';
const supabase = createClient(supabaseUrl, supabaseKey);

export default {
  components: {
    CommentForm,
  },
  methods: {
    async addComment(name, comment) {
      const { data, error } = await supabase
        .from('comments')
        .insert([{ name, comment }]);
      if (error) console.error(error);
      else console.log('Comment added:', data);
    }
  }
};
</script>

<template>
  <h1>Food</h1>
  <instrument/>
  <food-item/>
  <food-item/>
  <food-item/>
  <comment-form/>
  <comment/>
</template>

<style></style>
