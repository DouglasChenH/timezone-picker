<script>
/**
 * FormTimeZonePicker
 * Form TimeZonePicker component
 */
//- imports
var timezonePicker = require('timezone-picker')
var momentTimezone = require('moment-timezone')
/////////////////////////////////////////////////

var vue = {
    name: 'FormTimeZonePicker',
    props: {
        field: {
            type: Object,
            default: function() {
                return {}
            }
        }
    },
    data: function () {
        return {}
    },
    computed: {},
    mixins: [],
    methods: {
        callback: function(timezone) {
            if (this.field.value != timezone) {
                this.field.value = timezone   
            }
        }
    },
    ready: function () {
        this.$nextTick(function () {
            var options = {
                quickLink: [],
                // width : (type:number) Sets width of map.
                // height : (type:number) Sets height of map.
                // defaultCss : (type:boolean) No need to include css if it is true
                // hoverColor :(type:string) Shows color on hover
                // selectedColor :(type:string) Sets selected ** timezone** color
                // mapColor :(type:string) Sets map color
                // quickLink :(type:Array of string) Creates shortcuts to select zone ["IST","MST".......]
                // selectBox :(type:boolean) If it is set tofalse select box will not be created
                // showHoverText : (type:boolean) If it is set to false hover text will not be shown
                // hoverText: (type:function | string) text you want to show when you hover on map (works only if showHoverText is true)
                // mapHover : (type:string) by default it will show hovered polygon(area) on which mouse is pointed (value: timezone, country, zonename)
                // "timezone" : when you hover on map it will heighlight all are with same timezone
                // "country" : when you hover on map it will heighlight all are with same country code
                // "zonename" : when you hover on map it will heighlight all are with same zonename
            }
            $(this.$el).timezonePicker(options, this.callback)
            $(this.$el).data('timezonePicker').setValue(this.field.value)
        })
    },
    events: {}
}

module.exports = vue
</script>

<template lang="jade">
div(style='width:50%;overflow:auto')
    label.control-label Time Zone
</template>

<style type="text/css" >
</style>
