# 🌐 WordPress Contact Form 7
## Pass Values from One Form to Another

## 🖥️ Screenshots
### Form 1
<img src="https://a.imagem.app/dTdG8.png" alt="dTdG8.png" border="0" width="300"/>

### CF7 Form 1 Code:
```
<label> Φόρμα 1 </label>
<label> Αριθμός Παιδιών
    [number* children_num] </label>

<label> Αριθμός Ενηλίκων
    [number* parent_num] </label>

<label> Μήνας 
    [number* choose_month] </label>

<label> Έτος
    [number* choose_year] </label>

[submit "Επόμενο"]
```

### Form 2
<img src="https://a.imagem.app/dTRMi.png" alt="dTRMi.png" border="0" width="300"/>

### CF7 Form 2 Code:
```
<label> Φόρμα 2 </label>
<label> Όνομα
    [text* your_name] </label>

<label> Τηλέφωνο
    [tel* phone_num] </label>

<label> Αριθμός Παιδιών
    [number* children_num default:get] </label>

<label> Αριθμός Ενηλίκων
    [number* parent_num default:get] </label>

<label> Μήνας
    [number* choose_month default:get] </label>

<label> Έτος
    [number* choose_year default:get] </label>

[submit "Αποστολή"]
```

## ❗️Important Part❗️
### Pass Values from Form 1 to Form 2 and Redirect to Form 2

#### Put On 👨‍💻 function.php 👩‍💻
```
function vc_dom_event_footer() {
?>
<script type="text/javascript">
document.addEventListener( 'wpcf7mailsent', function( event ) {
    if ( '188' == event.detail.contactFormId ) { // 188 = CF7 Form ID
         var inputs = event.detail.inputs;
		 for ( var i = 0; i < inputs.length; i++ ) {
			 if ( 'children_num' == inputs[i].name ) {
				var children_num = inputs[i].value;
			 }
			 if ( 'parent_num' == inputs[i].name ) {
				var parent_num = inputs[i].value;
			 }
			 if ( 'choose_month' == inputs[i].name ) {
				var choose_month = inputs[i].value;
			 }
			 if ( 'choose_year' == inputs[i].name ) {
				var choose_year = inputs[i].value;
			 }
		 }
		 window.location.href = '/?page_id=178/'+'&children_num='+children_num+'&parent_num='+parent_num+'&choose_month='+choose_month+'&choose_year='+choose_year;
    }else if ( '190' == event.detail.contactFormId ) { // 190 = CF7 Form ID
		 window.location.href = '/?page_id=178/';
    }
}, false );
</script>
<?php
}
add_action( 'wp_footer', 'vc_dom_event_footer' );
```
#### What this function doing ⁉️
Basically, add inserted values from Form 1 to Form 2 link and with `default:get` passing the values to fields also redirect to Form 2.

## Images of use:
### Form 1:
<img src="https://a.imagem.app/dTVeC.png" alt="dTVeC.png" border="0" width="300"/>

### Link of Form 2:
<img src="https://a.imagem.app/dTvpN.png" alt="dTvpN.png" border="0" width="500"/>

### Form 2:
<img src="https://a.imagem.app/dT4LY.png" alt="dT4LY.png" border="0" width="300"/>
