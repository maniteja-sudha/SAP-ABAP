## ABAP Program: Parameters and Select-Options Example

```abap
REPORT zparam_selectopt_demo.

TABLES: mara.

PARAMETERS: p_matnr TYPE mara-matnr.
SELECT-OPTIONS: s_matnr FOR mara-matnr.

DATA: it_mara TYPE STANDARD TABLE OF mara,
      wa_mara TYPE mara.

SELECT * FROM mara
  INTO TABLE it_mara
  WHERE matnr = p_matnr
     OR matnr IN s_matnr.

IF sy-subrc <> 0.
  MESSAGE 'No materials found for the given input' TYPE 'I'.
  EXIT.
ENDIF.

LOOP AT it_mara INTO wa_mara.
  WRITE: / 'Material:', wa_mara-matnr,
         'Type:', wa_mara-mtart,
         'Industry:', wa_mara-mbrsh.
ENDLOOP.
```
