## Bitstamp.calculator : A javascript code to calculate gains in crypto exchanges
To check the functionality of this code refer to the article: [nepy.pe/en/bitstamp.calculator.](http://www.nepy.pe/en/crypto/invest-in-cryptocurrencies-basic-math-to-start-winning/) 

There are two ways to use this code:
1. Website
2. Wordpress

### Website

Download the file `bitcalc_EN.html` and is ready to use.

### Wordpress

1. Copy the following lines to your `functions.php` page in your Wordpress theme
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


### Instructions:
i)

# Install in a website

# Install in

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](https://github.com/statsconchris/bitstamp.calculator/tree/English) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://github.com/statsconchris/bitstamp.calculator/tree/English).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/statsconchris/nepy_bitCalculator/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
