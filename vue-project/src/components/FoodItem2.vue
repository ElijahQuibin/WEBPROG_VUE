<template>
    <div class="container">
        <div class="mango">
            <h2>{{ name }}</h2>
            <p>{{ message }}</p>
        </div>
    </div>
</template>

<script>
export default {
    data() {
      return {
        name: 'Apples',
        message: 'I like apples'
      }
    }
};
</script>

<style>
.container {
    display: flex;
    flex-direction: row; /* Changed from column to row */
}
.mango {
    border: dashed black 1px;
    margin: 10px;
    padding: 10px;
    background-color: lightgreen;
}
</style>