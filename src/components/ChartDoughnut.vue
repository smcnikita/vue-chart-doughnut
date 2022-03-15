<script>
export default {
	name: 'ChartDoughnut',
	props: {
		per: {
			type: String,
			required: true,
		},
		color: {
			type: String,
			required: false,
			default: '#726A95',
		},
		colorBg: {
			type: String,
			required: false,
			default: '#e1e1e1',
		},
		/** text size in px (default: 32px) */
		textSize: {
			type: String,
			required: false,
			default: '32',
		},
	},
	methods: {
		getChartLine() {
			const per = parseInt(this.per);
			let textSize = this.textSize + 'px';
			let base = this.colorBg;
			let color = this.color;

			let deg = (per / 100 * 360) + 'deg';
			let deg1 = '90deg';
			let deg2 = deg;
			let base2 = base;
			let center = '#fff';
			let color2 = color;
			let textColor = '2B2B2B';

			if ( per < 50 ) {
				deg1 = (per / 100 * 360 + 90) + 'deg';
				deg2 = '0deg';

				base = color;
				color = base2;
				color2 = base2;
			}

			this.$refs.donutChart.style.background = base;
			this.$refs.sliceOne.style.transform = 'rotate(' + deg1 + ')';
			this.$refs.sliceOne.style.background = color;
			this.$refs.sliceTwo.style.transform = 'rotate(' + deg2 + ')';
			this.$refs.sliceTwo.style.background = color2;
			this.$refs.chartCenter.style.background = center;
			this.$refs.perTitle.innerHTML = per + '%';
			this.$refs.perTitle.style.color = textColor;
			this.$refs.perTitle.style.fontSize = textSize;
		},
	},
	mounted() {
		this.getChartLine();
	},
};
</script>

<template>
	<div class="chart__wrapper">
		<div class="donut__chart" ref="donutChart">
			<div class="donut__slice slice__one" ref="sliceOne"></div>
			<div class="donut__slice slice__two" ref="sliceTwo"></div>
			<div class="chart__center" ref="chartCenter">
				<span class="chart__title" ref="perTitle"></span>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
@use "sass:math";

$size: 148px;
$sizeHalf: math.div($size, 2);
$width: 22px;

.chart__wrapper {
	float: left;
	background: #fff;
}

.donut__chart {
	width: $size;
	height: $size;
	position: relative;
	border-radius: 50%;
	overflow: hidden;

	.donut__slice {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;

		&.slice__one {
			clip: rect(0 $size $sizeHalf 0);
		}

		&.slice__two {
			clip: rect(0 $sizeHalf $size 0);
		}
	}

	.chart__center {
		position: absolute;
		border-radius: 50%;
		top: $width;
		left: $width;
		width: $size - ($width * 2);
		height: $size - ($width * 2);

		span {
			display: block;
			text-align: center;
			font-weight: bold;
			line-height: $size - ($width * 2);
		}
	}
}

.chart__title {
	user-select: none;
	font-family: inherit;
}
</style>
