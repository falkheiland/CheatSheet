# ecoDMS

## regex examples

### Rechnungsnr./-datum 181030022 / **`01.10.2018`**

`REGEX:(?i)(?<=Rechnungsnr\.\/-datum\s{1}\d{9}\s{1}\/\s{1})\b([\S]+)\b`

### Rechnungsnr./-datum **`181030022`** / 01.10.2018

`REGEX:(?i)(?<=Rechnungsnr\.\/-datum\s{1})\b([\S]+)\b`

### Unfallversicherung Nr.: **`400 665 212 `** dsfrg 0ß09 2545

`REGEX:(?i)(?<=Unfallversicherung Nr.:\s{1})\b([\d|\s]+)\b`

### Kunde **`1361162`**

`REGEX:(?i)(?<=Kunde\s{1})\b([\S]+)\b`

### Herrn **`Max Mustermann Hauptstraße 1 01234 Musterstadt`**

`REGEX:(?i)(?<=Herrn\s{1})\b(.+)\b`

### Firma **`Rechnung`** INNA Ihre Referenznr. 2003274521

`REGEX:(?i)(\bRechnung\b)`

### Amtsgericht Dresde **`Cyberport GmbH`** E-Mail Am

`REGEX:(?i)(\bCyberport GmbH\b)`

### Servicekosten DE S2 1 19,0 % Gesamtbetrag **`207,90`** EUR amtbetrag enthalten

`REGEX:(?i)(?<=Gesamtbetrag\s{1})\d+(,|.)\d+`

### 324 3423 334 Text **`18.10.2017`** Text 23,12

`REGEX:\d{2}.\d{2}.\d{4}`

### Datum **`7. Dezember 2018`** Durchwahl Tlf3444

`REGEX:\d{1,2}.\s{1}\w+\s{1}\d{4}`

### Str. 1 **`197,59`** EUR leistung

`REGEX:\d{1,4},\d{2}`

### 0,00 EUR

`REGEX:\d{1,4},\d{2}\s+EUR`
