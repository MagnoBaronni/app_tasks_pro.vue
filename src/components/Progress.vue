<template>
    <div class="progress">	
	<span class="progress-value">{{progress}}%</span>
    <div class="progress-bar" :style="{width: progress + '%'}"></div>
    </div>
</template>

<script>
 export default {
    props: {
        progress:{
           type: Number,
          default:  0 }
    }
 }
</script>
<style>
.progress{
    position: relative;
    width: 80%;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 15px;
    border: 1px solid #fff;   
    color: #fff;
}
.progress-bar{
    position: absolute;
    height: 100%;
    border-radius: 8px;
    align-self: flex-start;
    background-color: #4caf50;
}
.progress-value{
    z-index: 1;
    font-size: 1.5rem;
}


</style>