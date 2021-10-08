<template>
    <div class="wrapper-stepper">
        <div class="stepper">
            <div class="stepper-progress">
                <div class="stepper-progress-bar" :style=" 'width:' + stepperProgress ">
                </div>
            </div>
            <div class="stepper-item" :class="{'current': step == item, 'success': step > item}" v-for="item in 4" :key="item">
                <div class="stepper-item-couter">
                    <img class="icon-success" src="@/assets/check-lg.svg" alt="">
                    <span class="number">
                        {{item}}
                    </span>
                </div>
                <span class="stepper-item-title">
                    Passo {{item}}
                </span>
            </div>
        </div>

        <div class="stepper-content">
            <div class="stepper-pane" v-if="step == 1">
                <h3>form 1</h3>
            </div>
            <div class="stepper-pane" v-else-if="step == 2">
                <h3>form 2</h3>
            </div>
            <div class="stepper-pane" v-else-if="step == 3">
                <h3>form 3</h3>
            </div>
            <div class="stepper-pane" v-else-if="step == 4">
                <h3>form 4</h3>
            </div>
        </div>

        <div class="controls">
            <button class="btn" @click="step--" :disabled="step === 1">Anterior</button>
            <button class="btn btn--green-1" @click="step++" :disabled="step===4">Seguinte</button>
        </div>
    </div>
</template>

<script>
export default {
    components:{
    },
    data(){
        return {
            step:1
        }
    },
    computed:{
        stepperProgress(){
            return (100 / 3) * (this.step -1 ) + '%'
        }
    }
}
</script>

<style lang="scss" scoped>
.wrapper-stepper{
    background-color: #FBDE40;
    padding: 60px;
    border-radius: 32px;
    box-shadow: rgba($color: #000000, $alpha: 1.0);

    .stepper{
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 660px;
        position: relative;
        z-index: 0;
        margin-bottom: 24px;

        .stepper-progress{
            position: absolute;
            background-color: #fff;
            height: 2px;
            z-index: -1;
            left: 0;
            right: 0;
            margin: 0 auto;

            .stepper-progress-bar{
                position: absolute;
                left: 0;
                height: 100%;
                width: 0%;
                background-color: #000;
                transition: .4s all ease;
            }
        }
    }

    .stepper-item{
        display: flex;
        flex-direction: column;
        align-items: center;
        color: #000;
        transition: .3s all ease;

        &-couter{
            height: 60px;
            width: 60px;
            display: grid;
            align-items: center;
            justify-content: center;
            background-color: #fff;
            border-radius: 100%;
            border: 2px solid #000;
            position: relative;


            .icon-success{
                position: absolute;
                opacity: 0;
                transform: scale(0);
                transition: .3s all ease;
            }

            .number{
                font-size: 22px;
                transition: .3s all ease;
            }
        }
        
        &-title{
            position: absolute;
            font-size: 14px;
            bottom: -24px;
        }
    }


    .stepper-item.success{
        .stepper-item-couter{
            border-color: #fff;
            background-color: green;
            color: #fff;
            font-weight: 600;
            display: flex;

            .icon-success{
                opacity: 1;
                transform: scale(1);
            }

            .number{
                opacity: 0;
                transform: scale(0);
            }
        }

        .stepper-item-title{
            color: green;
        }
    }


    .stepper-item.current{
        .stepper-item-couter{
            border-color: green;
            background-color: green;
            color: #fff;
            font-weight: 600;
        }

        .stepper-item-title{
            color: #818181;
        }
    }

    .stepper-pane{
        color: #333;
        text-align: center;
        padding: 120px 60px;
        box-shadow: 0 8px 12px rgba($color: #000000, $alpha: 1.0);
        margin: 40px 0;
    }

    .controls{
        display: flex;
        gap: 1rem;
        justify-content: space-between;

        .btn{
            background-color: #818181;
            color: #fff;
            &:disabled{
                opacity: 0.5;
                pointer-events: none;
            }

        }

        &--green-1{
            background-color: green;
            border-color: green;
            color: #fff;
        }
    }
    
}


</style>