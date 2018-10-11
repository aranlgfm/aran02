<template>
    <div>
        <div class="feelBtns">
            <vue-pikaday id="datePut" v-model="now" :options="pikadayOptions" :autoDefault="true"/>
            <input id="feelSet" type="text" readonly="readonly" v-model="feelState"/>
            <button class="btns" v-on:click="bad()">bad</button>
            <button class="btns" v-on:click="soso()">soso</button>
            <button class="btns" v-on:click="good()">good</button>
        </div>
        <div>
            <input id="comm" type="text" v-model="contents.comment"/>
            <button id="saveBtn" v-on:click="save()">{{saveBtn}}</button>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
	data() {
		return {
			// 날짜, 감정, 간략한 감상
			pikadayOptions: {
				format: 'YYYY MMM DD',
			},
			feelState: '',
			saveBtn: '+',
			now: null,
			contents: {
				date: '',
				feel: 0,
				comment: '',
			},
		};
	},
	methods: {
		bad() {
			this.contents.feel = 1;
			this.feelState = 'bad';
			console.log(this.contents.feel + '<<<<<<<test');
		},
		soso() {
			this.contents.feel = 2;
			this.feelState = 'soso';
			console.log(this.contents.feel + '<<<<<<<test');
		},
		good() {
			this.contents.feel = 3;
			this.feelState = 'good';
			console.log(this.contents.feel + '<<<<<<<test');
		},
		save() {
			console.log('save start');
			this.contents.date = moment(this.now).format('YYYY MMM DD');
			console.log('comment : ' + this.comment + ':::: feel : ' + this.feel + ':::: date : ' + this.contents.date);
			axios
				.post('http://localhost:3001/add', this.contents, {
					'Access-Control-Allow-Origin': '*',
					'content-type': 'application/json',
				})
				.then(res => {
					console.log(res.data);
				});

			// 화면 리로드. 이정도로 일단 만족. 추후 수정할 것
			location.reload();
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