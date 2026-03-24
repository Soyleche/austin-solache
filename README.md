# austin-solache
README file about.... me!

Contact Information:
austinsolache@gmail.com
https://github.com/Soyleche
www.linkedin.com/in/austinsolache

Coding Languages
JavaScript
HTML/CSS
MySql
Python

Projects:
<!DOCTYPE html>
<html>
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Calculator Project</title>
    <link rel="stylesheet" href="calculator.css">
    <link rel="icon" href="./favicon.ico" type="image/x-icon">
        <script>
            let firstOperand = "";
            let secondOperand = "";
            let operator = "";
            let answer = "";
            let str = "";
            let display = " 0 ";
            // Inserts first operand + operator + second operand
            function operand(input) { 
                // if statement checks if input is a finite Number to start and operator is Null then enters firstOperand
                if (Number.isFinite(input) === true && operator == "")  {
                    str = input.toString();
                    firstOperand = firstOperand + str ;
                    str = "";
                }
                 // else if checks operator isn't null to enter the secondOperand
                else if (Number.isFinite(input) === true && operator != "") {
                    str = input.toString();
                    secondOperand = secondOperand + str ;
                    str = ""; 
                }
                document.getElementById("box").innerHTML = firstOperand + operator + secondOperand;
            } 
            
            // Multiple else if to display firstOperand and operator (+, -, *, /)
            function operation(input) {    
                if (secondOperand === "") {    
                    operator = input;
                    document.getElementById("box").innerHTML = firstOperand + operator;
                }    
            }
            
            // Makes Operands into negative #, percent, and adds decimal points.
            function special(input) {       
                if (input === "+/-" && operator == "" && !firstOperand.includes("-") && firstOperand != "") {
                    firstOperand =  "-" + firstOperand;
                }
                else if (input === "+/-" && operator != "" && !secondOperand.includes("-") && secondOperand != "") {
                    secondOperand = "-" + secondOperand;
                }
                else if (input === "." &&  (!firstOperand.includes(".")) && (!firstOperand.includes("%"))) {
                    firstOperand = firstOperand + ".";
                }
                 else if (input === "." && operator != "" && (!secondOperand.includes(".")) && (!secondOperand.includes("%"))) {
                    secondOperand = secondOperand + ".";
                }
                else if (input === "%" && (!firstOperand.includes("%")) && operator == "" && firstOperand != "") {
                    firstOperand = firstOperand + "%";
                }
                else if (input === "%" && (!secondOperand.includes("%")) && operator != "" && secondOperand != "") {
                    secondOperand = secondOperand + "%";
                }  
                document.getElementById("box").innerHTML =  firstOperand + operator + secondOperand;

                 if (input === "c") {
                    firstOperand = "";
                    secondOperand = "";
                    operator = "";
                    document.getElementById("box").innerHTML = "0";
                } 
            }

            // Does the arithmetic for Addition, Subtraction, Multiplication, and Divsion
            function math() {    
            // Checks if Operands are percentages and converts them to decimals
                if (firstOperand.includes("%")) {
                    firstOperand = .01 * firstOperand.replace("%", "");
                    } 
                    
                if (secondOperand.includes("%")) {
                    secondOperand = .01 * secondOperand.replace("%", "");
                }

                firstOperand = Number(firstOperand);
                secondOperand = Number(secondOperand);
                
                if (operator === " + ") { 
                    answer = firstOperand + secondOperand;
                    answer = Math.ceil(answer * 100) / 100;
                    }
                else if (operator === " - ") {
                    answer = firstOperand - secondOperand;
                    answer = Math.ceil(answer * 100) / 100;
                    }
                else if (operator === " x ") {
                    answer = firstOperand * secondOperand;
                    answer = Math.ceil(answer * 100) / 100;
                    }
                else if (operator === " ÷ ") {
                    answer = firstOperand / secondOperand;
                    answer = Math.ceil(answer * 100) / 100;
                    }
                    document.getElementById("box").innerHTML = answer;
                    firstOperand = answer.toString();
                    secondOperand = '';
                }
        </script>
    </head>
    <body>      
        <section id="calculator">
            <section id="input-box">
                <p id="box">0</p>
            </section>
            <section id="buttons">
                <button onclick="special('c')"> C </button>
                <button onclick="special('+/-')"> +/- </button>
                <button onclick="special('%')"> % </button>
                <button onclick="operation(' ÷ ')"> ÷ </button>
                <button onclick="operand(7)"> 7 </button>
                <button onclick="operand(8)"> 8 </button>
                <button onclick="operand(9)"> 9 </button>
                <button onclick="operation(' x ')"> X </button>
                <button onclick="operand(4)"> 4 </button>
                <button onclick="operand(5)"> 5 </button>
                <button onclick="operand(6)"> 6 </button>
                <button onclick="operation(' - ')"> - </button>
                <button onclick="operand(1)"> 1 </button>
                <button onclick="operand(2)"> 2 </button>
                <button onclick="operand(3)"> 3 </button>
                <button onclick="operation(' + ')"> + </button>
                <button id="zero" onclick="operand(0)"> 0 </button>
                <button onclick="special('.')"> . </button>
                <button onclick="math()"> = </button>
            </section>
        </section>    
    </body>
</html>
