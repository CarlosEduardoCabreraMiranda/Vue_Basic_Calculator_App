<template>
    <div class="card text-center">
        <div class="card-body">
            <h4 class="card-title">Calculator</h4>
            <!--<div class="input">
                <div class="input-group">
                    <span class="input-group-text"></span>-->

            <div id="input" class="form-control text-center text-white">{{ current || '0' }}</div>
            <!--</div>
            </div>-->
            <div class="calculator-body">
                <button @click="clear()">C</button>
                <button @click="sign">+/-</button>
                <button @click="percent">%</button>
                <button @click="division" class="btn-warning text-white">÷</button>
                <button @click="append('7')">7</button>
                <button @click="append('8')">8</button>
                <button @click="append('9')">9</button>
                <button @click="multiplication" class="btn-warning text-white">x</button>
                <button @click="append('4')">4</button>
                <button @click="append('5')">5</button>
                <button @click="append('6')">6</button>
                <button @click="substraction" class="btn-warning text-white">-</button>
                <button @click="append('1')">1</button>
                <button @click="append('2')">2</button>
                <button @click="append('3')">3</button>
                <button @click="addition()" class="btn-warning text-white">+</button>
                <button @click="append('0')">0</button>
                <button @click="append('(')">(</button>
                <button @click="append(')')">)</button>
                <button @click="dot">.</button>
                <button @click="evaluateExpressionI(current)" class="btn-warning text-white equal">=</button>

            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Calculator_App',

    props: {
        value: { default: '', type: String }
    },

    data() {
        return {
            current: '12345',
            signed: false,
        }
    },
    methods: {
        //Aritmethic operations
        clear() {
            this.current = '';
        },

        sign() {
            this.current = this.current.charAt(0) === "-" ?
                this.current.slice(1) : `-${this.current}`
                this.signed = !this.signed;
        },

        percent() {
            const validOperators = ['+', '-', '*', '/'];
            if(this.current.includes(validOperators)){
            this.current = `${parseFloat(this.current) / 100}`
            }else{
                const lastNumber = this.current.split(/[+\-*/]/).pop();
                const percentage = lastNumber / 100;
                this.current = this.current.replace(new RegExp(lastNumber + "$"), percentage.toString());
            }
        },

        addition() {
            if (this.validSign('+')) {
                this.append('+');
            }
        },

        substraction() {
            if (this.validSign('-')) {
                this.append('-');
            }
        },

        multiplication() {
            if (this.validSign('*')) {
                this.append('*');
            }
        },

        division() {
            if (this.validSign('/')) {
                this.append('/');
            }
        },

        dot() {
            if (this.validSign('.')) {
                this.append('.');
            }
        },


        //Validations
        validSign(sign) {
            const lastCharacter = this.current.slice(-1);
            const validOperators = ['+', '-', '*', '/','.','(',')'];

            // Comprueba si el último carácter es un número y si el signo es un operador válido
            if (/^\d+$/.test(lastCharacter) && validOperators.includes(sign) || lastCharacter === ')') {
                // Si el último carácter es un número y el signo es un operador válido, permite el signo
                return true;
            } else {
                // Si el último carácter no es un número o el signo no es un operador válido, no permite el signo
                return false;
            }
        },

        especialChar(char){

            const lastCharacter = this.current.slice(-1);
            const especialCharacters = ['\n', '=', 'b', 's','p','(',')'];

            if (/^\d+$/.test(lastCharacter) && especialCharacters.includes(char)) {
                // Si el último carácter es un número y el signo es un operador válido, permite el signo
                return true;
            } else {
                // Si el último carácter no es un número o el signo no es un operador válido, no permite el signo
                return false;
            }
        },

        specialMethodsApply(char){
            switch (char) {
                case '\n':
                    this.clear();
                    break;
                case '=':
                    this.evaluateExpression(this.current);
                    break;
                case 's':
                    this.sign();
                    break;
                case 'p':
                    this.percent();
                    break;
                case 'b':
                    if(!this.validOperators){
                    this.current = this.current.slice(0,-1);
                    }else{
                        this.current = this.current.slice(0, -4);
                    }
                    break;
                case '(':
                    this.append('(');
                    break;
                case ')':
                    this.append(')');
                    break;
                default:
                    // Handle invalid operators (optional)
                    break;
            }

        },

        



            //Expression test and logics
            evaluateExpression(expression) {
                // Split the expression by operators (+, -, *, /, %)
                const terms = expression.split(/([+\-*/])/).filter(term => term.trim() !== '');

                // Initialize the result with the first term
                let result;

                if(terms[0] === '-'){
                     result = Number(eval(expression));
                }else{
                    result = parseFloat(terms[0]);
                }
                    
                // Iterate through the remaining terms
                for (let i = 1; i < terms.length; i += 2) {
                    const operator = terms[i];
                    const nextTerm = parseFloat(terms[i + 1]);

                    switch (operator) {
                        case '+':
                            result += nextTerm;
                            break;
                        case '-':
                            result -= nextTerm;
                            break;
                        case '*':
                            result *= nextTerm;
                            break;
                        case '/':
                            result /= nextTerm;
                            break;
                        default:
                            // Handle invalid operators (optional)
                            break;
                    }
                }

                this.current = String(result);
                return result;
            },



            append(number) {

                this.current = `${this.current}${number}`
            },



            evaluateExpressionI(expression){
                try{
                    const result = parseFloat(eval(expression));
                    this.current = result.toString();
                    return result;
                }catch(error){
                    return "Error al evaluar la expresión matemática.";
                }
            }
            

            /*filterTxt() {
                this.current = this.current.replace(/[^0-9./%-+e]/g, '-');
    
                if ( this.repetidos(this.current,true)|| this.current.startsWith(".")) {
                     this.current = this.current.replace(/[^0-9./%-+e]/g, '-');
                }
                if (this.current.endsWith("-") || this.current.endsWith(".")) {
                    this.current = this.current.replace(/[^0-9/%+]/g, '');
                }
            }
            
            ,*/

        },

        mounted() {
            window.addEventListener('keydown', (event) => {
                const char = event.key;
                if ((char >= '0' && char <= '9') || this.validSign(char)) {
                    this.append(char);
                }else if (this.especialChar(char)){
                    this.specialMethodsApply(char)
                }
            });
        },
        beforeUnmount() {
            window.removeEventListener('keydown', this.event);
        }
    }
        
    
</script>

<style>
#input {
    background-color: black;
    font-size: 30px;
}

.calculator-body {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-size: 40px;
}

.equal{
    grid-column: 1/5;
}



#black {
    color: black;
}

</style>