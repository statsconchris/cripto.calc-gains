## Bitstamp.calculator : A javascript code to calculate gains in crypto exchanges
To check the functionality of this code refer to the article: [nepy.pe/en/bitstamp.calculator.](http://www.nepy.pe/en/crypto/invest-in-cryptocurrencies-the-basic-math-of-trading-fees-to-start-winning/) 

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
					var pbVal = document.getElementById("Pb").value;
					var psVal = document.getElementById("Ps").value;
					var ibVal = document.getElementById("Ib").value;
					var isVal = document.getElementById("Is").value;
					var qVal = document.getElementById("Q").value;

					var result = (psVal * qVal * (1 - (isVal / 100) )) - (pbVal * qVal * (1 + (ibVal / 100) ));
					document.getElementById("Result").value = result;
				    }
        </script>
		<script type="text/javascript">
                    function bitcalc2() {
					var pb2Val = document.getElementById("Pb2").value;
					var ib2Val = document.getElementById("Ib2").value;
					var is2Val = document.getElementById("Is2").value;

					var result2 = pb2Val * (+is2Val + +ib2Val) / (100 - (1*is2Val)) ;
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
                    <label>Buying price (Pb):</label>
                    <input id="Pb" type="text" placeholder="" />
                    <label>Selling price (Ps):</label>
                    <input id="Ps" type="text" placeholder="" />
                    <label>Buying fee (Ib):</label>
                    <input id="Ib" type="text" placeholder="" />
                    <label>Selling fee (Is):</label>
                    <input id="Is" type="text" placeholder="" />
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
                    <label>Buying price (Pb):</label>
                    <input id="Pb2" type="text" placeholder="" />
                    <label>Buying fee (Ib):</label>
                    <input id="Ib2" type="text" placeholder="" />
                    <label>Selling fee (Is):</label>
                    <input id="Is2" type="text" placeholder="" />
                    <label></label>
                    <input id="Run" onClick='bitcalc2()' type="button" value="Calculate" />
                    <label></label>
                    <input id="Result2" style="font-style: italic; padding-left: -2px;" readonly="readonly" type="text" value="The minimal growth is..." />
            </div>
```


