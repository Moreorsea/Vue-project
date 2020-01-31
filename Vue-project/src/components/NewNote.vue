<template>
  <div class="new-note">
	<label>Title</label>
        <input type="text" v-model="newNote.title">

		<!--Priority-->
		<label>Priority</label>
		<select v-model="newNote.priority">
			<option @click="selectPriority('normal')" value="normal">Стандартный</option>
			<option @click="selectPriority('important')" value="important">Важный</option>
			<option @click="selectPriority('critical')" value="critical">Критичный</option>
		</select>

		<label>Description</label>
				<textarea v-model="newNote.descr"></textarea>
				<button class="btn btnPrimary" @click="addNote">New note</button>
			</div> 
</template>

<script>
  export default {
	props: {
		newNote: {
			type: Object,
			required: true
		}
	},
	methods: {
		addNote() {
			this.$emit('addNote', this.newNote)
		},
		selectPriority(value) {
			this.value = value

		}
	}
  }
</script>

<style lang="scss">
	.new-note {
		text-align: center;
	}

	.btn.btnPrimary {
		margin: 20px 0;
	}
	label > textarea {
		margin-top: 20px;
	}
	select {
		width: 100%;
		padding: 10px;
		border-radius: 20px;
		margin-bottom: 20px;
	}
</style>