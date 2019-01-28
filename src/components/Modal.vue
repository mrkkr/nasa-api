<template>
	<div class="modal-wrapper">
		<div class="inner-wrapper">
			<div class="close" v-on:click="$emit('closeModal')"></div>
			<div class="photo">
				<img v-bind:src="photo" />
			</div>
			<div class="description">
				<h2 class="title">{{ title }}</h2>
				<p class="date">
					<strong>created:</strong> {{ date }}
				</p>
				<p class="description">
					{{ desc }}
				</p>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
  	item : {
  		type: Object,
  		required: true,
  	},
  },
  data() {
  	return {
  		photo: null,
  		title: null,
  		desc: null,
  		date: null,
  	};
  },
  mounted() {
  	this.photo = this.item.links[0].href;
	  this.title = this.item.data[0].title;
	  this.desc = this.item.data[0].description.substring(0,200);
	  this.date = this.item.data[0].date_created;
  }
};
</script>

<style lang="scss" scoped>
	.modal-wrapper {
		max-width: 100%;
		height: 100%;
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		background-color: #f6f6f6;
		overflow-y: auto;

		.title {
			color: #3272ab;
		}

		@media (min-width: 1024px) {
			max-width: 70%;
			height: 60%;
			bottom: 0;
			margin: auto;
			box-shadow: 0 30px 30px -10px rgba(0,0,0, .3);
		}

		.inner-wrapper {
			display: flex;
			justify-content: center;
			align-items: center;
			flex-direction: column;
			height: 100%;

			@media (min-width: 0px) {
				padding: 23px;
			}
			@media (min-width: 991px) {
				padding: 50px;
			}
			@media (min-width: 1024px) {
				flex-direction: row;

				.photo {
					min-width: 50%;
					margin-right: 20px;
				}
			}

			.photo {
				height: auto;
				background: transparent;

				img {
					@media (min-width: 0px) {
						max-width: 100%;
    				height: auto;
					}
					@media (min-width: 991px) {
						max-height: 510px;
					}
				}
			}
			.description {
				color: #333;
			}
		}
		.close {
			position: absolute;
			width: 30px;
			height: 30px;
			padding: 30px;
			top: 0;
			right: 0;
			cursor: pointer;

			&::before,
			&::after {
				position: absolute;
				top: 30px;
				right: 20px;
				content: '';
				width: 20px;
				height: 2px;
				background: #000;
				display: block;
			}
			&::before {
				transform: rotate(45deg);
			}
			&::after {
				transform: rotate(-45deg);
			}
		}
	}
</style>