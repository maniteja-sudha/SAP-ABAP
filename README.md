# SAP-ABAP
Program-code.

# PROGRAM FOR SELECETION SCREEN 
# PARAMETER # SELECT OPTION.



REPORT zparam_selectopt_demo.

*--- Declare table reference for MARA (Material Master - General Data)
TABLES: mara.

*--- User inputs
PARAMETERS: p_matnr TYPE mara-matnr.  "Single value input
SELECT-OPTIONS: s_matnr FOR mara-matnr.  "Multiple values/ranges input

*--- Internal table & work area for storing fetched data
DATA: it_mara TYPE STANDARD TABLE OF mara,
      wa_mara TYPE mara.

*--- Fetch data from MARA based on parameter or select-option
SELECT * FROM mara
  INTO TABLE it_mara
  WHERE matnr = p_matnr
     OR matnr IN s_matnr.

*--- Check if any records were found
IF sy-subrc <> 0.
  MESSAGE 'No materials found for the given input' TYPE 'I'.
  EXIT.
ENDIF.

*--- Display fetched data
LOOP AT it_mara INTO wa_mara.
  WRITE: / 'Material:', wa_mara-matnr,
         'Type:', wa_mara-mtart,
         'Industry:', wa_mara-mbrsh.
ENDLOOP.
