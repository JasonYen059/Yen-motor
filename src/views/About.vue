<template>
  <div id="about">
    <div class="text">
      <img class="yen-img" src="../../public/yencustom.png" />
      <p>
        Since 2021, Lorem ipsum dolor sit amet, consectetur adipiscing gravida
        mauris. Fusce ornare ornare semper. Quisque pretium. elit. Nullam et
        tempus dolor, et gravida metus. Nullam id
      </p>
    </div>
  </div>
</template>

<style scoped>
#about {
  background-image: url("../../public/door.jpg");
  background-size: cover;
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

p {
  font-size: 1.2rem;
  width: 70%;
  text-align: center;
  margin: 50px auto;
  color: #ebebeb;
}

.text {
  width: 100%;
  height: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.yen-img{
  margin-top: 2vw;
  width: 30%;
  height: auto;
}
</style>
