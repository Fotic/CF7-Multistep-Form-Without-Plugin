# WordPress Contact Form 7
## Pass Values from one form to another

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
    [number* children_num watermark default:get] </label>

<label> Αριθμός Ενηλίκων
    [number* parent_num default:get] </label>

<label> Μήνας
    [number* choose_month default:get] </label>

<label> Έτος
    [number* choose_year default:get] </label>

[submit "Αποστολή"]
```
