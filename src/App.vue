<template>
  <div id="app">
    <!-- <img src="./assets/tofeel.jpg"> -->
    <h1>Today's Feeling</h1>

    <router-view/>

	<h2 class="footer">Welcome to Today's Feeling</h2>
  </div>
</template>

<script>
export default {
	name: 'App',
};
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

h1 {
	font-weight: normal;
	font-family: 'Kodchasan', sans-serif;

	/* 상단고정 */
	position: absolute;
	left: 0;
	top: 0;
	width: 100%;
	margin: 0;
	padding: 15px 0;
	text-align: center;
	color: white;
	/* background: #7fba0a; */
	background: gray;
}

.footer {
	font-weight: normal;
	font-family: 'Kodchasan', sans-serif;
	position: absolute;

	/* 하단고정 */
	left: 0;
	bottom: 0;
	width: 100%;
	margin: 0;
	padding: 10px 0;
	text-align: center;
	color: white;
	/* background: #7fba0a; */
	background: gray;
}
</style>
