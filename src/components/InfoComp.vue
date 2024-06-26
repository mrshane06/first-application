<template lang="">
    <!-- <div>
        {{firstName}} {{lastName}} {{objectData}}
    </div> -->
    <h1>This is a component</h1>
    <slot></slot>
</template>
<script>
export default {
    // props: ['firstName','lastName', 'objectData']
    props:{
        objectData:Object,
        firstName:String,
        lastName:String
    }
 // same thing as above
}
</script>
<style>
    
</style>