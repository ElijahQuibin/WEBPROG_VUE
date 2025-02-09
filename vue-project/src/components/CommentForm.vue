<template>
    <div>
      <h2>Leave a Comment</h2>
      <CommentForm @submit-comment="submitComment" />
      <div v-if="submissionStatus" class="mt-2">
        {{ submissionStatus }}
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { supabase } from '../lib/supabaseClient'
  import CommentForm from './CommentForm.vue';
  
  const submissionStatus = ref(null);
  
  // Your Supabase URL and Key - IMPORTANT!
  const tableName = 'comments'; // Name of your Supabase table
  
  async function submitComment(name, comment) {
    submissionStatus.value = "Submitting...";
    try {
      const { error } = await supabase
        .from(tableName)
        .insert([{ name, comment }]);
  
      if (error) {
        console.error("Error inserting comment:", error);
        submissionStatus.value = "Error submitting comment. Please try again.";
      } else {
        submissionStatus.value = "Comment submitted successfully!";
      }
    } catch (err) {
      console.error("An unexpected error occurred:", err);
      submissionStatus.value = "An unexpected error occurred. Please try again later.";
    }
  }
  </script>
  
  <style scoped>
  /* Basic styling - Customize as needed */
  .form-group {
    margin-bottom: 1rem;
  }
  
  label {
    display: block;
    margin-bottom: 0.5rem;
  }
  
  .form-control {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .btn {
    padding: 0.5rem 1rem;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  </style>