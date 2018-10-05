<template>
<div id="app">
    <!-- <table id="userList">
        <th>objectid</th>
        <th>userid</th>
        <th>username</th>
        <tr v-for="feel in feels" v-bind:key="feel._id">
            <td>{{feel.feeltext}}</td>
        </tr>
    </table> -->
	<li v-for="(item, index) in tes12" v-bind:key="index">{{item.tesname}} + asfd</li>
	<div>--------------------------</div>
	<li v-for="(item, index) in feels" v-bind:key="index">{{item}} + asfd</li>
    <div>aran test {{feels}}</div>
</div>
</template>

<script>
import axios from 'axios';
import { parse, patch } from 'semver';

export default {
	name: 'app',
	data() {
		return {
			feels: [],
			tes12: [{ tesname: 'test1', tesmimi: 'test123' }, { tesname: 'test2', tesmimi: 'test111' }],
		};
	},
	mounted() {
		this.getList();
	},
	methods: {
		getList: () => {
			axios
				.get('http://localhost:3001/')
				.then(res => {
					this.feels = res.data.feels;

					// res.data.feels.forEach(element => {
					// 	// console.log(element);
					// 	this.feels = element;
					// });
					// this.feels = Object.setPrototypeOf(this.feels);
					console.log(this.feels);
				})
				.catch(e => {
					console.log(e);
				});
		},
	},
};
</script>
