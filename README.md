####OXID List details preview module

You can copy all files from the copy_this folder to their respective location,
if you have a vanilla 4.5.* OXID eShops CE installation.

Enable module under System:  
details.php => ib_list_detail_preview.php

####Requirements:  
the javascript requires jQuery & jQueryUI  
```<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.0/jquery.js"></script>   
   <script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.8.16/jquery-ui.min.js" type="text/javascript"></script>
```             
Merge the CSS from changed_full into your CSS.  
Copy the templates from changed_full into your tpl dir. (resp. merge into your templates)  
Include this inc file everywhere you want to use the preview and where you use the modified product box  
f.e.  
out/basic/tpl/inc/list.tpl:  
```[{ include file="inc/list_detail_preview.tpl" }]
```  
add the data attribute to every box of the class .product:  
    data-ib_list_details_preview-anid="[{$product->getID()}]"  
f.e.:  
inc/product.tpl  
```<div [{if $test_Cntr}]id="test_cntr_[{$test_Cntr}]_[{$product->oxarticles__oxartnum->value}]"[{/if}] class="product hproduct[{if $head}] head[{/if}] [{$size|default:''}] [{$class|default:''}]">
```  
==>  
```<div [{if $test_Cntr}]id="test_cntr_[{$test_Cntr}]_[{$product->oxarticles__oxartnum->value}]"[{/if}] class="product hproduct[{if $head}] head[{/if}] [{$size|default:''}] [{$class|default:''}]" data-ib_list_details_preview-anid="[{$product->getID()}]">
```  

Clear /tmp    
```cd tmp  
rm -f *
``` 

####Caution:
The template is just rudimentary styled, please contribute a proper styling for the basic template, if somebody wants to volunteer?!


--------------------------------------------------------------------
Released under 
MIT License
(i.e., do whatever you want with this and use at your own risk)
