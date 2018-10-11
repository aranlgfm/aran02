<template>
<div id="list">
    <table id="userList">
        <th>날짜</th>
        <th>기분</th>
        <th>기분설명</th>
        <tr v-for="feel in feels" v-bind:key="feel._id">
            <td>{{feel.feeldate}}</td>
            <td>{{feel.feelfeel}}</td>
            <td>{{feel.feeltext}}</td>
        </tr>
    </table>
</div>
</template>

<script>
import axios from 'axios';
import { parse, patch } from 'semver';
import Axios from 'axios';

export default {
	name: 'list',
	data() {
		return {
			feels: null,
		};
	},
	mounted() {
		this.getList();
	},
	methods: {
		getList() {
			Axios.get('http://localhost:3001/')
				.then(res => {
					this.feels = res.data;
				})
				.catch(e => {
					console.log(e);
				});
		},
		pri() {
			console.log('success !!!!!!!!!!!!!!!!');
		},
	},
};

export const pri = () => {
	console.log('pri start');
};
</script>
