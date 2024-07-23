# ZTE-F601 tagparam

Persistant items are stored in usercfg partition and in tagparam partition.
Tagparams can be viewed using:

```
# cat /proc/tagparam_m/tagitem 

ParamId: 0x891                                
Param:                                        
30 Param End                                  
ParamId: 0x880                                
Param:                                        
5a 54 45 47 Param End                         
ParamId: 0x8001                               
Param:                                        
54 be 53 99 58 17 Param End 
...

```

Some parameters are accessible from the web, some are not.

## TagParam values

```
0x100 dbPersonInitHostNameProduct (looks like MAC address) \
0x200 SerialNumber
0x300 ManuFacturerOui
0x601 dbPersonInitAuthUserNameProduct
0x701 dbPersonInitAuthPasswordProduct
0x804 HardwareVerTag
0x860 VendorID
0x881 VendorSpecific
0x882 password
0x883 register_id
0x884 dbDefGPONCFG
0x890 OnuMode
0x891 FactoryHLTmode
0x894 VersionConfigTypeFromTagParam
0x896 falsify_defend_mode
```


## ZTE software version (6.0.2)

The displayed software version of the ZTE F6.0.1 is a summation of the actual SW version and the OnuMode.
For example, If the OneMode is "1" (0x31), the displayed SW version is 6.0.2.

OneMode can be modified by directly writing to address 0x890
