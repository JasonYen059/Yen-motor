<template>
  <div id="about">
    <div class="text">
      <img src="../../public/yencustom.png" width="380px" height="auto">
      <p> Since 2021, Lorem ipsum dolor sit amet, consectetur adipiscing gravida mauris. Fusce ornare ornare semper. Quisque pretium. elit. Nullam et tempus dolor, et gravida metus. Nullam id </p>
    </div>
  </div>
</template>

<style scoped>
  #about {
    background-image: url('../../public/door.jpg');
    background-size: cover;
    position: absolute;
    top: 0;
    box-sizing: border-box;
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-items: center;
    align-items: center;
    }
  
  p {
    font-size: 18px;
    width: 500px;
    text-align: center;
    margin:  150px auto;
    color: #ebebeb;
  }

  .text {
    margin:70px 0 0 30px;
    width: 800px;
    height: 600px;
    display: flex;
    flex-direction: column;
    justify-items: center;
    align-items: center;
  }
</style>
