validaciones-javascript
=======================
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html>
    <head>
        <title>TODO supply a title</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width">
    </head>
    <body onload="factura()" bgcolor="#AA5533">
        
            <h4> INGRESE NUMEROS PARA VERIFICAR SI SON PRIMOS:</h4> 
           
           <input type="text"  style="background-color : #E6E6FA;text-align:center" size="7" name="valor1" id="valor1" />
           <input type="button" name="Aceptar" value="Aceptar" onclick="esPrimos()" id="Aceptar"/>
           <p id="resultado" ></p>
           
           <h4> INGRESE NUMERO DE CEDULA:</h4> 
           <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="cedIngresada"  />
           <input type="button" id="ingresar" value="ingresar" onclick="Cedula()"/><br>
          
             <h4> SUMA BINARIA:</h4> 
              <label>Primer valor binario:</label>
              <input type="text"  style="background-color : #E6E6FA;text-align:center" size="15" id="bina1"/><br>
              <label>Segundo valor binario:</label>
              <input type="text"  style="background-color : #E6E6FA;text-align:center" size="15" id="bina2"/><br>
        <input type="button" id="Sumar" value="Sumar" onclick="sumaBinarios(document.getElementById('bina1').value,
                    document.getElementById('bina2').value)"/>
            
             <h4> INVERSION DE PALABRAS:</h4> 
             <label>Ingese palabras:</label>
        <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="ingpalabra1"/>
        <label>Palabra a invertir:</label>
        <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="ingpalabra2"/>
        <input type="button" id="invertir" value="invertir" onclick="Binarios(document.getElementById('ingpalabra1').value, document.getElementById('ingpalabra2').value)"/>
        <br>
        
    <center>
                     <h4> TIENDA ALIS:</h4> 
        Seleccionar cliente: <select id="listClient"></select><br>
        <hr size="8">
        Producto:  <select id="listProd"></select>
        Precio : <input type="text"  style="background-color : #E6E6FA;text-align:center" size="15" id="precioUnit" />
        Cantidad: <input type="text"  style="background-color : #E6E6FA;text-align:center" size="15" id="cantidad" onchange="total()"/>

        Total: <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="total"/>
        <input type="button" id="agregar" value="Agregar" onclick="FiladeProductoIngresado()"/><br>
        <hr size="5">

        <h4>Total de la compra: </h4>
        
        <div id="contenido">

        </div>
        <hr>
        Subtotal : <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="subtotal" value="0"/>
        IVA 12%: <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="iva"/>
        Descuento 5%: <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="descuento"/>
        Total Final: <input type="text" style="background-color : #E6E6FA;text-align:center" size="15" id="totalFinal"/>
    </center>
        
        
    </body>
    
</html>
<script>
    //numeros primos
 function esPrimos() {
                var data = document.getElementById("valor1").value;
                var ingreso = 0;
                for (i = 0; i <= data; i++) {
                    var residuo = data % i;
                    if (residuo == 0) {
                        ingreso++;
                    }
                }
                if (ingreso == 2 || data == 1) {
                    
                    document.getElementById("resultado").innerHTML = "el numero es Primo";
                } else {
                  document.getElementById("valor1").value= "";
                  document.getElementById("resultado").innerHTML = "el numero no es Primo";
                }
            }
            //ingreso numeros de cedula
             function Cedula()
            {
                var cedula = document.getElementById("cedIngresada").value;
                array = cedula.split("");
                num = array.length;
                if (num == 10)
                {
                    total = 0;
                    digito = (array[9] * 1);
                    for (i = 0; i < (num - 1); i++)
                    {
                        mult = 0;
                        if ((i % 2) != 0) {
                            total = total + (array[i] * 1);
                        }
                        else
                        {
                            mult = array[i] * 2;
                            if (mult > 9)
                                total = total + (mult - 9);
                            else
                                total = total + mult;
                        }
                    }
                    decena = total / 10;
                    decena = Math.floor(decena);
                    decena = (decena + 1) * 10;
                    final = (decena - total);
                    if ((final == 10 && digito == 0) || (final == digito)) {
                        alert("Cedula Valida");
                        return true;
                    }
                    else
                    {
                        alert("Cedula NO Valida");
                        return false;
                    }
                }
                else
                {
                    alert("La cedula consta de 10 digitos");
                    return false;
                }
            }
           
           //suma binaria
            function sumaBinarios(bUno, bDos) {
                var primeroEnDecimal = parseInt(bUno, 2);
                var segundoEnDecimal = parseInt(bDos, 2);
                var sumaDecimal = primeroEnDecimal + segundoEnDecimal;
                var sumaBinario = deci(sumaDecimal);
                alert('Resultado en decimal: ' + sumaDecimal + 'Resultado en Binario: ' + sumaBinario);
            }

            function deci(arg)
            {
                res1 = 999;
                args = arg;
                while (args > 1)
                {
                    arg1 = parseInt(args / 2);
                    arg2 = args % 2;
                    args = arg1;
                    if (res1 == 999)
                    {
                        res1 = arg2.toString();
                    }
                    else
                    {
                        res1 = arg2.toString() + res1.toString();
                    }
                }
                if (args == 1 && res1 != 999)
                {
                    res1 = args.toString() + res1.toString();
                }
                else if (args == 0 && res1 == 999)
                {
                    res1 = 0;
                }
                else if (res1 == 999)
                {
                    res1 = 1;
                }
                var ll = res1.length;
                while (ll % 4 != 0)
                {
                    res1 = "0" + res1;
                    ll = res1.length;
                }
                return res1;
            }
            
            //invertir numero binario
             function Binarios(fraseRecivida, palabraRecivida) {
                var palabras = fraseRecivida.split(" ");
                for (i = 0; i < palabras.length; i++) {
                    if (palabras[i] == palabraRecivida) {
                        alert(invertirpalabra(palabras[i]));
                    }
                }
            }
            function invertirpalabra(cadena) {
                var x = cadena.length;
                var cadenaInvertida = "";
                while (x >= 0) {
                    cadenaInvertida = cadenaInvertida + cadena.charAt(x);
                    x--;
                }
                return cadenaInvertida;
            }
            //factura
            function factura() {
                var clientes = ["Nexar", "Pedro", "Juan", "Evelin"];
                var productos = ["Aceite", "Cafe", "Pan", "Galleta"];
                var listaClientesDatos = document.getElementById('listClient');
                for (var i = 0; i < clientes.length; i++) {
                    var opt = document.createElement('option');
                    opt.innerHTML = clientes[i];
                    opt.value = clientes[i];
                    listaClientesDatos.appendChild(opt);
                }
                var listaProductosDatos = document.getElementById('listProd');
                for (var i = 0; i < productos.length; i++) {
                    var opt = document.createElement('option');
                    opt.innerHTML = productos[i];
                    opt.value = productos[i];
                    listaProductosDatos.appendChild(opt);
                }

            }
            function total() {
                var unitario = document.getElementById('precioUnit').value;
                var cantidad = document.getElementById('cantidad').value;
                var total = parseFloat(unitario) * parseFloat(cantidad);
                document.getElementById('total').value = total;
            }
            function FiladeProductoIngresado() {
                var subtotal = document.getElementById('subtotal').value;
                document.getElementById('subtotal').value = parseFloat(subtotal) + parseFloat(document.getElementById('total').value);
                var subtotalNuevo = document.getElementById('subtotal').value;
                document.getElementById('iva').value = parseFloat(subtotalNuevo) * 0.12;
                var ivaNuevo = document.getElementById('iva').value;
                document.getElementById('descuento').value = (parseFloat(subtotalNuevo) + parseFloat(ivaNuevo)) * 0.05;
                var descuentoNuevo = document.getElementById('descuento').value;
                document.getElementById('totalFinal').value = (parseFloat(subtotalNuevo) + parseFloat(ivaNuevo)) - parseFloat(descuentoNuevo);
                capotTexto = document.createElement('input');
                capotTexto.type = "text";
                capotTexto.name = "producto";
                capotTexto.id = "produc";
                capotTexto.value = document.getElementById('listProd').value + '     -     ' + document.getElementById('precioUnit').value + '     -     ' + document.getElementById('cantidad').value + '     -     ' + document.getElementById('total').value;
                capotTexto.size = "50";
                document.getElementById('contenido').appendChild(capotTexto);
                salto = document.createElement('br');
                document.getElementById('contenido').appendChild(salto);
            }
</script>            
