# ram4f28379d
external sram daughter card for tms320f28379 launchpad  LAUNCHXL-F28379D  V2.0 .

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




LAUNCHXL-F28379D hardware  modification:
add  0 Ohm resistance  to   R68 R70 R72  R74  R76 R78




Software fix: 
The  c2000ware exampls emif1_16bit_asram_cpu01 (EMIF1 module accessing 16bit ASRAM ,test 32kx16bit space)  can work .
The source must be modified  to test the whole 256k x 16bit   space.
 

1   modify two lines in the file to initilize address line a15  and a16.
"C:\ti\ccs900\c2000\C2000Ware_1_00_06_00\device_support\f2837xd\common\source\F2837xD_Emif.c"

    GPIO_SetupPinMux(88,cpu_sel,3);    
    GPIO_SetupPinMux(89,cpu_sel,3);   
   
   to 
   
    GPIO_SetupPinMux(88,cpu_sel,2);   //a15
    GPIO_SetupPinMux(89,cpu_sel,2);   //a16
   
   
 2   256k x 16bit sram can  contain  128k(0x20000)  32bit elements.  change ram size configuration in 
    
   "C:\ti\ccs900\c2000\C2000Ware_1_00_06_00\device_support\f2837xd\examples\cpu1\emif1_16bit_asram\cpu01\emif1_16bit_asram.c"
  
 
   #define ASRAM_CS2_SIZE       0x20000     
   

   
