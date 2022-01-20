<template>
  <div id="footer">
    <div>
      <p>Pending</p>
    </div>
    <div>
      <p>Passed</p>
    </div>
    <div>
      <p>Approved</p>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
#footer {
  display: flex;
  justify-content: center;
  gap: 10px;
  border: solid 1px aqua;
  padding: 5px;
  width: 15%;
  margin: 0 auto;
}

#footer p {
  font-size: 12px;
}
</style>
