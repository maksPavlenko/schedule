<template>
  <div class="schedule">
    <div 
      class="schedule__item"
      v-for="(pointItem, scheduleIndex) in schedulePoints"
			:class="`schedule__item--${pointItem}`"
      :key="scheduleIndex"
    >
			<div class="schedule__value">x:{{ scheduleIndex }} y:{{ pointItem }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Schedule',
  data() {
    return {
      schedulePoints: [5, 8, 2, 1, 15, 2, 3, 5, 9, 11, 10, 4, 3, 14, 1, 7, 10, 3, 2, 13]
    }
  }
}
</script>

<style lang="scss">
  .schedule {
		display: flex;
		align-items: flex-end;
		justify-content: flex-start;

    &__item {
			position: relative;

      $points: (1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15);
      
      @each $pointValue in $points {
        &--#{$pointValue} {
          height: 10px * $pointValue;
					width: 55px;
          margin: 0 10px;
					@if $pointValue <= 5 { 
						background-color: green; 
					} @else if $pointValue <= 10 {
						background-color: yellow;
					} @else {
						background-color: red;
					}  
        }
      }
    }
    
		&__value {
			position: absolute;
      width: 100%;
			bottom: -30px;
      font-size: 12px;
      text-align: center;
		}
  }
</style>

