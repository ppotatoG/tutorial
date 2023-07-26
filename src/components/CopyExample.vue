<template>
	<div>
		<ul>
			<li v-for="(item, index) in items" :key="index">
				<input v-model="item.name" type="text"/>
				<input v-model="item.checked" type="checkbox"/>
				<input v-model="item.gender" type="text"/>
			</li>
		</ul>
		<button @click="resetDeepCopy">Reset Deep Copy</button>
		<button @click="resetShallowCopy">Reset Shallow Copy</button>
	</div>
</template>

<script>

const defaultData = [
	{name: 'Alice', checked: false, gender: 'female'},
	{name: 'Bob', checked: true, gender: 'male'},
	{name: 'Charlie', checked: false, gender: 'male'},
	{name: 'Daisy', checked: true, gender: 'female'},
	{name: 'Edward', checked: false, gender: 'male'},
	{name: 'Fiona', checked: true, gender: 'female'},
	{name: 'George', checked: false, gender: 'male'},
	{name: 'Hannah', checked: true, gender: 'female'},
	{name: 'Ian', checked: false, gender: 'male'},
	{name: 'Jane', checked: true, gender: 'female'},
]

export default {
	name: 'CopyExample',
	data() {
		return {
			items: []
		};
	},
	created() {
		this.resetDeepCopy();
	},
	methods: {
		resetDeepCopy() {
			this.items = JSON.parse(JSON.stringify(defaultData));
			console.log(this.items)
			console.log(defaultData)
		},
		resetShallowCopy() {
			this.items = defaultData;
			console.log(this.items)
			console.log(defaultData)
		}
	}
};
</script>

<style>
ul {
	list-style: none;
}

li {
	display: flex;
	gap: 10px;
}
</style>
