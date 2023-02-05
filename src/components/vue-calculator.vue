<template>
    <div class="flex justify-center content-center w-full">
        <div class="">
            <input type="text" v-model="result" diabled
                class="w-full mb-6 h-24 rounded-t-md block text-right font-semibold text-2xl text-white md:text-3xl pr-3 bg-transparent outline-none hover:outline-none">

            <div class="grid grid-cols-4 gap-12 text-3xl text-white">
                <button class="text-amber-800 dark:bg-yellow-400 rounded-full" @click="clear">C</button>
                <button class="text-amber-800 dark:bg-yellow-400 rounded-full" @click="percent">%</button>
                <button class="text-amber-800 dark:bg-yellow-400 rounded-full " @click="invert">+/-</button>
                <button class="text-amber-800 dark:bg-yellow-400 rounded-full p-1" @click="setOperator('/')">/</button>
                <button class="bg-gray-600 rounded-full p-1 " @click="addNumber(7)">7</button>
                <button class="bg-stone-600 rounded-full p-1" @click="addNumber(8)">8</button>
                <button class="bg-gray-600 rounded-full p-1" @click="addNumber(9)">9</button>
                <button class="text-amber-800 dark:bg-yellow-400 rounded-full p-1" @click="setOperator('*')">*</button>
                <button class="bg-gray-600 rounded-full p-1" @click="addNumber(4)">4</button>
                <button class="bg-stone-600 rounded-full p-1" @click="addNumber(5)">5</button>
                <button class="bg-gray-600 rounded-full p-1" @click="addNumber(6)">6</button>
                <button class="text-amber-800 dark:bg-yellow-400 rounded-full p-1" @click="setOperator('-')">-</button>
                <button class="bg-gray-600 rounded-full p-1" @click="addNumber(1)">1</button>
                <button class="bg-stone-600 rounded-full p-1" @click="addNumber(2)">2</button>
                <button class="bg-gray-600 rounded-full p-1" @click="addNumber(3)">3</button>
                <button class="text-amber-800 dark:bg-yellow-400 rounded-full p-1" @click="setOperator('+')">+</button>
                <button class="bg-gray-600 rounded-full p-1" @click="addNumber(0)">0</button>
                <button class="bg-stone-600 rounded-full p-1" @click="addPoint">.</button>
                <button class="col-span-2 rounded-full text-amber-800 dark:bg-yellow-400 " @click="equal">=</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'vueCalculator',
    data: function () {
        return {
            result: 0,
            tmp_value: 0,
            reset: false,
            operator: undefined
        }
    },
    methods: {
        clear() {
            this.result = 0;
            this.tmp_value = 0;
            this.operator = undefined;
        },
        invert() {
            this.result *= -1;
        },
        percent() {
            this.result /= 100;
        },
        addNumber(number) {
            if (this.result == 0 || this.reset === true) {
                this.result = '';
                this.reset = false;
            }


            this.result += number.toString();
        },
        addPoint() {
            if (!this.result.includes('.'))
                this.result += '.';
        },
        setOperator(operator) {
            if(this.tmp_value != 0)
            this.calculate();

            this.tmp_value = this.result;
            this.operator = operator;
            this.reset = true;
        },
        equal() {
            this.calculate();
            this.tmo_value = 0;
            this.operator = undefined;
        },
        calculate() {
            let value = 0;
            let firstNum = parseFloat(this.tmp_value);
            let secondNum = parseFloat(this.result);

            switch(this.operator) {
                case '+':
                    value = firstNum + secondNum;
                    break;
                    case '-':
                        value = firstNum - secondNum;
                        break;
                        case '*':
                            value = firstNum * secondNum;
                            break;
                            case '/':
                                value = firstNum / secondNum;
            }

            this.result = value.toString();
        }
    }
}
</script>

<style scoped>

</style>