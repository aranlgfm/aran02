<template>
    <div>
        <input type="hidden" v-model="now" v-on="setDateToday()"/>
        <div class="feelBtns">
            <vue-pikaday id="datePut" v-model="now" :options="pikadayOptions"/>
            <input id="feelSet" type="text" readonly="readonly" v-model="feelState"/>
            <button class="btns" v-on:click="bad()">bad</button>
            <button class="btns" v-on:click="soso()">soso</button>
            <button class="btns" v-on:click="good()">good</button>
        </div>
        <div>
            <input id="comm" type="text" v-model="comment" v-on:keyup="commentPut()"/>
            <button id="saveBtn" v-on:click="save()">{{saveBtn}}</button>
        </div>
    </div>
</template>

<script>
export default {
	data() {
		return {
			// 날짜, 감정, 간략한 감상
			now: null,
			pikadayOptions: {
				format: 'YYYY MMM DD',
			},
			feel: 0,
			comment: '',
			feelState: '',
			saveBtn: '+',
		};
	},
	methods: {
		setDateToday() {
			// this.now = moment().format('DD MMM YYYY');
			// var ss = moment().format();
			// var ssss = ss.format('YYYY MMM DD');
			this.now = moment();
			console.log(moment() + '<<<<<<<<<<<<<<<<');
			// this.now = ss;
			// this.now = ssss;
		},
		bad() {
			this.feel = 1;
			this.feelState = 'bad';
			console.log(this.feel + '<<<<<<<test');
		},
		soso() {
			this.feel = 2;
			this.feelState = 'soso';
			console.log(this.feel + '<<<<<<<test');
		},
		good() {
			this.feel = 3;
			this.feelState = 'good';
			console.log(this.feel + '<<<<<<<test');
		},
		commentPut() {
			console.log(this.comment + 'test');
		},
		save() {
			console.log('save start');
		},
	},
};
</script>


<style>
.btns {
	background-color: whitesmoke;
	border: 2px solid gainsboro;
	color: gray;
	text-align: center;
	display: inline-block;
	-webkit-transition-duration: 0.4s;
	transition-duration: 0.4s;
	width: 60px;
	height: 30px;
	padding: 0px;
	margin-top: 10px;
	margin-bottom: 5px;
	border-radius: 15px;
	outline: none;
	font-family: 'Kodchasan', sans-serif;
	font-size: 100%;
}

.btns:hover {
	background-color: gray;
	color: white;
	/* border: 2px solid dodgerblue; */
	border: 2px solid gray;
}

#saveBtn {
	background-color: gray;
	border: 2px solid gray;
	color: white;
	text-align: center;
	display: inline-block;
	-webkit-transition-duration: 0.4s;
	transition-duration: 0.4s;
	width: 34px;
	height: 34px;
	/* padding: 0px; */
	margin-top: 10px;
	margin-bottom: 5px;
	border-radius: 17px;
	outline: none;
	font-family: 'Kodchasan', sans-serif;
	font-size: 70%;
}

#saveBtn:hover {
	background-color: white;
	color: gray;
	/* border: 2px solid dodgerblue; */
	border: 2px solid gray;
}

#feelSet {
	background-color: gray;
	border: 2px solid gray;
	color: white;
	text-align: center;
	display: inline-block;
	-webkit-transition-duration: 0.4s;
	transition-duration: 0.4s;
	width: 70px;
	height: 30px;
	padding: 0px;
	margin-top: 10px;
	margin-bottom: 5px;
	border-radius: 25px;
	outline: none;
	font-family: 'Kodchasan', sans-serif;
	font-size: 100%;
}

#comm {
	background-color: white;
	border: 2px solid gray;
	color: gray;
	text-align: left;
	display: inline-block;
	-webkit-transition-duration: 0.4s;
	transition-duration: 0.4s;
	width: 400px;
	height: 30px;
	/* padding: 0px; */
	padding-left: 10px;
	margin-top: 10px;
	margin-bottom: 5px;
	border-radius: 25px;
	outline: none;
	font-family: 'Kodchasan', sans-serif;
	font-size: 100%;
}

#datePut {
	background-color: white;
	border: 2px solid gray;
	color: gray;
	text-align: center;
	display: inline-block;
	-webkit-transition-duration: 0.4s;
	transition-duration: 0.4s;
	width: 150px;
	height: 30px;
	padding: 0px;
	margin-right: 20px;
	margin-top: 10px;
	margin-bottom: 5px;
	border-radius: 25px;
	outline: none;
	font-family: 'Kodchasan', sans-serif;
	font-size: 100%;
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