# Calculadora JavaScript

Esta calculadora te permite ejecutar las cuatro operaciones basicas que son: sumar, restar, multiplicar y dividir, adicionalmente cuenta con la funcion de resetear los resultados en caso de querer realizar una nueva operación

al ingresar un dato se mostrara en pantalla y se guardara para realizar la operacion y desaparecera al ingresar el segundo dato, no te afanes! cada datos queda guardado a menos que actives la funcion de resetear
##CODIGO
###HTML
Creamos una tabla que sera nuestra calculadora, la primera fila ocupara las cuatro columnas, esta sera la pantalla que nos muestra los datos ingresados y el resultado. En las siguientes cuatros filas estaran ubicados los numeros, operadores y demas botones que haran efectivo su funcionamiento

-----
En la etiqueta body estara incluido el atributo onload="init()" esto hara que una vez acabe de cargar la pagina se mande a llamar el metodo init que se encontrara en el codigo  de javascript.

```html
<body onload="init();">
    <table class="calculadora">
        <tr>
            <td colspan="4"><span id="resultado"></span></td>
        </tr>
        <tr>
            <td><button class="botones"id="siete">7</button></td>
            <td><button class="botones"id="ocho">8</button></td>
            <td><button class="botones"id="nueve">9</button></td>
            <td><button class="botones"id="division">/</button></td>
        </tr>
        <tr>
            <td><button class="botones"id="cuatro">4</button></td>
            <td><button class="botones"id="cinco">5</button></td>
            <td><button class="botones"id="seis">6</button></td>
            <td><button class="botones"id="multiplicacion">*</button></td>
        </tr>
        <tr>
            <td><button class="botones"id="uno">1</button></td>
            <td><button class="botones"id="dos">2</button></td>
            <td><button class="botones"id="tres">3</button></td>
            <td><button class="botones"id="resta">-</button></td>
        </tr>
        <tr>
            <td><button class="botones"id="igual">=</button></td>
            <td><button class="botones"id="reset">C</button></td>
            <td><button class="botones"id="cero">0</button></td>
            <td><button class="botones"id="suma">+</button></td>
        </tr>
        <tr>
            <td colspan="4"><span id="creador">Karen Cisneros</span></td>
        </tr>
    </table>
<script src="script.js"></script>
</body>
```
###CSS
Haremos que la tabla parezca una calculadora, uno de los estilos mas importantes lo aplicamos al pasar el click encima de cada boton para asegurarnos de cada boton clickeado :)

```css
.calculadora{
    display:block;
    margin:0 auto;
    padding:20px;
    background-color:#297bb9;
    width:350px;
    height:530px;
    border-radius: 25px;
  }
  .calculadora td button{
    display:block;
    width:70px;
    height: 70px;
    font-size: 25px;
  }
  .botones{
    border-radius: 8px;
    border: none;
  }
  .botones:hover{
    cursor: pointer;
    background-color: #206396;

  }
  #creador{
    display:block;
    padding-top:20px;
    color:#fff;
    text-align: center;
    width:300px;
  }
  #resultado{
    display:block;
    text-align: center;
    font-size: 40px;
    margin-bottom: 50px;
    width:300px;
    height: 100px;
    line-height: 100px;
    background-color:#fff;
    border-radius: 25px;
    overflow-y: scroll;
  }
```
####Javascript
Para realizar las operaciones crearemos 3 variables en las que se guardaran el primer dato. el segundo dato y el resultado de la operacion
```javascript
var operandoa;
var operandob;
var operacion;
```
Dentro de la funcion init guardaremos los elementos del documento HTML por medio de su id
```
function init(){
  //variables
  var resultado = document.getElementById('resultado');
  var reset = document.getElementById('reset');
  var suma = document.getElementById('suma');
  var resta = document.getElementById('resta');
  var multiplicacion = document.getElementById('multiplicacion');
```
Asi con cada numero y operador
----
Creamos la funcion de limpiar, resetear y resolver

```
function limpiar(){
    resultado.textContent = "";
}
function resetear(){
    resultado.textContent ="";
    operandoa = 0;
    operandob = 0;
    operacion = "";
}
function resolver(){
    var res= 0;
    switch (operacion){
        case "+":
            res = parseFloat(operandoa) + parseFloat(operandob);
            break;
        case "-":
            res = parseFloat(operandoa) - parseFloat(operandob);
            break;
        case "*":
            res = parseFloat(operandoa) * parseFloat(operandob);
            break;
        case "/":
            res = parseFloat(operandoa) / parseFloat(operandob);
            break;       
    }
    resetear();
    resultado.textContent = res;
}
```

###End