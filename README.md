## Invertir en criptomonedas. La matemática de las comisiones
Considerando la plataforma Bitstamp, detallamos la matemática básica de las comisiones de compra y venta y discutimos el crecimiento mínimo necesario para empezar a ganar. Los cálculos fueron desarrollados en JavaScript.
<hr>

**Instrucciones**

Dos soluciones: `Website` y `Wordpress`.

##### 1. Website

Descargar el archivo `calc-gains.html` y listo.

##### 2. Wordpress

2.1. Copiar el siguiente código en `functions.php` ubicado en tu editor de tema en Wordpress

```javascript
function wpb_hook_javascript() {
  if (is_single ('80')) { 
    ?>
        <script type="text/javascript">
                    function bitcalc() {
					var pcVal = document.getElementById("Pc").value;
					var pvVal = document.getElementById("Pv").value;
					var icVal = document.getElementById("Ic").value;
					var ivVal = document.getElementById("Iv").value;
					var qVal = document.getElementById("Q").value;

					var result = (pvVal * qVal * (1 - (ivVal / 100) )) - (pcVal * qVal * (1 + (icVal / 100) ));
					document.getElementById("Resultado").value = result;
				    }
        </script>
		<script type="text/javascript">
                    function bitcalc2() {
					var pc2Val = document.getElementById("Pc2").value;
					var ic2Val = document.getElementById("Ic2").value;
					var iv2Val = document.getElementById("Iv2").value;

					var result2 = pc2Val * (+iv2Val + +ic2Val) / (100 - (1*iv2Val)) ;
					document.getElementById("Resultado2").value = result2;
				    }
        </script>
    <?php
  }
	  
}
add_action('wp_head', 'wpb_hook_javascript');
```
**Notar que el código superior no tiene las etiquetas de apertura y cierre de PHP. Esto está bien. No modificar. `functions.php` no requiere estas etiquetas.**

2.2 Reemplazar `80` en `is_single('')` con el id de tu post 

2.3 Añadir el siguiente código en tu post (html):
```html
        <h1>El primer cálculo</h1>
            <div id="content">
                <h3>Calculando la ganancia:</h3>
                    <label>Precio de compra (Pc):</label>
                    <input id="Pc" type="text" placeholder="" />
                    <label>Precio de venta (Pv):</label>
                    <input id="Pv" type="text" placeholder="" />
                    <label>Comisión de compra (Ic):</label>
                    <input id="Ic" type="text" placeholder="" />
                    <label>Comisión de venta (Iv):</label>
                    <input id="Iv" type="text" placeholder="" />
                    <label>Cantidad (Q):</label>
                    <input id="Q" type="text" placeholder="" />
                    <label></label>
                    <input id="Run" onClick='bitcalc()' type="button" value="Calcular" />
                    <label></label>
                    <input id="Resultado" style="font-style: italic; padding-left: -2px;" readonly="readonly" type="text" value="La ganancia es..." />
            </div>
        
        <h1>El segundo cálculo</h1>
            <div id="content">
                <h3>Calculando el crecimiento mínimo para empezar a ganar:</h3>
                    <label>Precio de compra (Pc):</label>
                    <input id="Pc2" type="text" placeholder="" />
                    <label>Comisión de compra (Ic):</label>
                    <input id="Ic2" type="text" placeholder="" />
                    <label>Comisión de venta (Iv):</label>
                    <input id="Iv2" type="text" placeholder="" />
                    <label></label>
                    <input id="Run" onClick='bitcalc2()' type="button" value="Calcular" />
                    <label></label>
                    <input id="Resultado2" style="font-style: italic; padding-left: -2px;" readonly="readonly" type="text" value="El crecimiento mínimo es..." />
            </div>
```


**Información**
  
- Para ver el funcionamiento del código, ir la artículo: 
  
  [Invertir en criptomonedas. La matemática de las comisiones](https://nepy.pe/article.php?pid=62648b9fa8293&lan=es).


