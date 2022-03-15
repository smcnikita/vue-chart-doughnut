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
	<div class="chart-wrapper d-flex justify-content-center">
		<div class="donut-chart chart" ref="donutChart">
			<div class="slice one" ref="sliceOne"></div>
			<div class="slice two" ref="sliceTwo"></div>
			<div class="chart-center" ref="chartCenter">
				<span class="chart-title" ref="perTitle"></span>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
@use "sass:math";

$size: 148px;
$sizeHalf: math.div($size, 2);
$width: 22px;

.chart-wrapper {
	float: left;
	background: #fff;
	padding: 20px;
	width: 100%;
}

// Donut Chart Mixin
.donut-chart {
	position: relative;
	border-radius: 50%;
	overflow: hidden;

	.slice {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}

	.chart-center {
		position: absolute;
		border-radius: 50%;

		span {
			display: block;
			text-align: center;
			font-weight: bold;
		}
	}
}

.donut-chart {
	&.chart {
		width: $size;
		height: $size;

		.slice {
			&.one {
				clip: rect(0 $size $sizeHalf 0);
			}

			&.two {
				clip: rect(0 $sizeHalf $size 0);
			}
		}

		.chart-center {
			top: $width;
			left: $width;
			width: $size - ($width * 2);
			height: $size - ($width * 2);

			span {
				line-height: $size - ($width * 2);
			}
		}
	}
}

.chart-title {
	user-select: none;
}
</style>
