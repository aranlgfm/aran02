<template>
  <div class="hello">
	  <div id="head"></div>
	  <button id="addBtn" name="addBtn" v-on:click="addClick()">{{add}}</button>
	  <component :is="whichComp"></component>
	  <div><button id="addBtn" v-on:click="testFu()">test btn</button></div>
	  <feelist></feelist>

  </div>
</template>

<script>
import put from './put';
import feelist from './list';

export default {
	name: 'HelloWorld',
	data() {
		return {
			add: '추가하기',
			puttest: '',
			onClick: 0,
		};
	},
	components: {
		put,
		feelist,
	},
	methods: {
		addClick() {
			if (this.onClick == 0) {
				this.onClick = 1;
			} else {
				this.onClick = 0;
			}
			console.log('add click');
		},
		testFu() {
			console.log('test fu start');
		},
	},
	computed: {
		whichComp() {
			switch (this.onClick) {
				case 1:
					return put;
				default:
					return null;
			}
			return null;
		},
	},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#head {
	margin: 70px;
}

#addBtn {
	background-color: gray;
	border: 2px solid gray;
	color: white;
	text-align: center;
	display: inline-block;
	-webkit-transition-duration: 0.4s;
	transition-duration: 0.4s;
	width: 100px;
	height: 40px;
	padding: 0px;
	margin: 10px;
	border-radius: 25px;
	outline: none;
	font-family: 'Nanum Pen Script', cursive;
	font-size: 150%;
}

@media (max-width: 600px) {
	#addBtn {
		font-size: 170%;
	}
}

#addBtn:hover {
	background-color: white;
	color: gray;
	/* border: 2px solid dodgerblue; */
	border: 2px solid gray;
}
/* 폰트 스타일
font-family: 'Kodchasan', sans-serif;
font-family: 'Notable', sans-serif;
font-family: 'Spirax', cursive;
font-family: 'Cedarville Cursive', cursive;
font-family: 'Josefin Sans', sans-serif;
font-family: 'Srisakdi', cursive;
font-family: 'Shadows Into Light', cursive;
font-family: 'Acme', sans-serif;
*/
</style>
