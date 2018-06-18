<template>
    <div :class="[classWrapper, width, 'relative']">      
        <input type="text" required="required" class="fw">
        <span class="span-icon" v-if="iconName">
            <i class="material-icons md-dark md-24">{{iconName}}</i>
        </span>
        <span class="bar fw block relative"></span>                
        <label class="inline-block">{{label}}</label>
        <div 
            class="validations-area fw f-f_cw"
            v-if="allValidation">
            <div 
                class="validation-area flex j-c_sbetween" 
                v-for="(validation, index) in allValidation" 
                :key="index"
                :style="validation.type === 'error' ? 'color: rgb(252, 100, 45)' : 'color: rgb(0, 166, 153)'">
                <div 
                    class="validation-icon-area inline-f j-c_center a-i_center">
                    <i class="material-icons md-18">
                        {{type(index)}}
                    </i>
                </div>
                <div 
                    class="validation-text-area inline-f j-c_center">
                    {{ validation.text }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            width: {
                default: 'fw'
            },
            classWrapper: {
                required: true,
                default: 'b-form-item'
            },
            required: {
                default: false
            },
            iconName: {
                default: 'person_outline'
            },
            label: {
                default: 'label',
                required: true
            },
            allValidation: {
                type: Array
            }
        },
        computed: {
            type() {
                return (index) => this.allValidation[index].type === 'error' ? 'close' : 'done'
            }
        }
    }
</script>

<style lang="scss" scoped>
@import '@/scss/_forms.scss';

.b-form-item{ 
    position: relative; 
    margin-bottom:30px;
    background-color: yellow;
    label{        
        left:5px;
        top:5px;
    }
    input{
        border-bottom:1px solid #757575;
    }
    /* BOTTOM BARS ================================= */
    .bar:before, .bar:after{
        content:'';
        height:1px; 
        width:0;
        bottom:1px; 
        position:absolute;
        background:#6200ee; 
        transition:0.2s ease all; 
        -moz-transition:0.2s ease all; 
        -webkit-transition:0.2s ease all;
    }
    .bar:before {
        left:50%;
    }
    .bar:after {
        right:50%; 
    }
    /* active state */
    input:focus ~ .bar:before, input:focus ~ .bar:after {
        width:50%;
    }
    /* active state */
    input:focus ~ label, input:valid ~ label 		{
        display: inline;
        top:-15px;
        font-size:14px;
        color:#5264AE;
    }
    

    .span-icon{
        display: inline-flex;
        position: absolute;
        padding-top: 3px;
        top: 0px;
        right: 0px;
        width: 30px;
        justify-content: center;
        align-items: center;
    }
}
.o-form-item{
    border: 1px solid #DBDBDB; 
    margin-bottom: 30px;
    position: relative;
    border-radius: 5px;
    background-color: yellow; 
    &:focus-within{
        border: 1px solid #008489;
    }
    label{        
        left:15px;
        background-color: red;
        top: 50%;
        bottom: 50%;
        display: inline-flex;
        align-items: center;
    }
    input{        
        padding:10px;
        border-radius: 5px;
    }
    input:focus ~ label, input:valid ~ label 		{
        display: inline;
        top:-9px;
        bottom: auto;
        font-size:14px;
        color:#5264AE;
        padding: 0 3px;
    }
    .span-icon{
        display: inline-flex;
        position: absolute;
        top: 0px;
        right: 0px;
        height: 100%;
        width: 30px;
        justify-content: center;
        align-items: center;
        background-color: red;
    }
}
form{width: 300px;}
input{
    font-size:19px;
    font-weight: 300;
    line-height: 24px !important;
    padding:5px;
    padding-right: 30px;
    width: 100%;
    border:none;
    color: rgb(72, 72, 72);
}
input:focus{ outline:none; }

/* LABEL ======================================= */
label 				 {
    padding: 0px;
    color:#999; 
    font-size:1em;
    font-weight:normal;
    position:absolute;
    pointer-events:none;
    transition:0.2s ease all; 
    -moz-transition:0.2s ease all; 
    -webkit-transition:0.2s ease all;
}

/* VALIDATIONS AND ERROR CHECKS ============================= */
.validations-area{
    margin-top: 3px;
}
.validation-area{
    padding: 5px 0 0 0;
    color: rgb(252, 100, 45);
    font-size: 14px;
}
.validation-icon-area{
    width: 30px;
}
.validation-text-area{
    flex: 1;
}
</style>

