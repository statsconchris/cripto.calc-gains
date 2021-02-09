## Bitstamp.calculator : A javascript code to calculate gains in crypto exchanges
To check the functionality of this code refer to the article: [nepy.pe/en/bitstamp.calculator.](http://www.nepy.pe/en/crypto/invest-in-cryptocurrencies-basic-math-to-start-winning/) 

There are two ways to use this code:
1. Website
2. Wordpress

### Website

Download the file `bitcalc_EN.html` and is ready to use.

### Wordpress

1. Copy the following code to `functions.php` page in your Wordpress theme
```markdown
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
					document.getElementById("Result").value = result;
				    }
        </script>
		<script type="text/javascript">
                    function bitcalc2() {
					var pc2Val = document.getElementById("Pc2").value;
					var ic2Val = document.getElementById("Ic2").value;
					var iv2Val = document.getElementById("Iv2").value;

					var result2 = pc2Val * (+iv2Val + +ic2Val) / (100 - (1*iv2Val)) ;
					document.getElementById("Result2").value = result2;
				    }
        </script>
    <?php
  }
	  
}
add_action('wp_head', 'wpb_hook_javascript');
```
**Notice that the above code doesn't have opening and closing PHP tags. This is ok! Do not change it. functions.php doesn't require these tags.**

2. Replace 80 in is_single('') with your post id

3. Add the following code to your post (html):
```markdown
	<h1>First calculation</h1>
            <div id="content">
                <h3>Calculate gain:</h3>
                    <label>Buying price (Pc):</label>
                    <input id="Pc" type="text" placeholder="" />
                    <label>Selling price (Pv):</label>
                    <input id="Pv" type="text" placeholder="" />
                    <label>Buying fee (Ic):</label>
                    <input id="Ic" type="text" placeholder="" />
                    <label>Selling fee (Iv):</label>
                    <input id="Iv" type="text" placeholder="" />
                    <label>Quantity (Q):</label>
                    <input id="Q" type="text" placeholder="" />
                    <label></label>
                    <input id="Run" onClick='bitcalc()' type="button" value="Calculate" />
                    <label></label>
                    <input id="Result" style="font-style: italic; padding-left: -2px;" readonly="readonly" type="text" value="The gain is..." />
            </div>
        
        <h1>Second calculation</h1>
            <div id="content">
                <h3>Calculate the minimal growth to start winning:</h3>
                    <label>Buying price (Pc):</label>
                    <input id="Pc2" type="text" placeholder="" />
                    <label>Buying fee (Ic):</label>
                    <input id="Ic2" type="text" placeholder="" />
                    <label>Selling fee (Iv):</label>
                    <input id="Iv2" type="text" placeholder="" />
                    <label></label>
                    <input id="Run" onClick='bitcalc2()' type="button" value="Calculate" />
                    <label></label>
                    <input id="Result2" style="font-style: italic; padding-left: -2px;" readonly="readonly" type="text" value="The minimal growth is..." />
            </div>
```


