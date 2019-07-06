# ram4f28379d
external sram daughter card for tms320f28379 launchpad  LAUNCHXL-F28379D.

This  daughter card  dose not work on emif2, then it dose not work on TMDSCNCD28379D.

files discription:

buttom.jpg         picture of buttom side.
eaglefiles.zip     eagle design files ,can open by eagle v6.6 and v7.7.
gerbfiles.zip      gerb file.
memboard.pdf       pdf of sch.
top.jpg            picture of top side.




bom:

IC1  : IS61WV25616EDBLL-10T .
P1   : DF40HC(4.0)-60DS-0.4V(51).

R10 R11: 47K resistance, 10k may woks too.

c9 c10 2.2uf.
c1    10uf, refer to ti's design in "C:\ti\ccs900\c2000\C2000Ware_1_00_06_00\boards\TIDesigns\F28379D_EMIF_DC". the c104 in sch ig bug

