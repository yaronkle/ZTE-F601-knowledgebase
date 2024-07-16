# ZTE-F601 sendcmd

Control of many ZTE features can be done directly through the shell using the sendcmd utility.
telnet the device and use sendcmd  

## Basic usage

```
# sendcmd
sendcmd :
  -pc show        : show all APPID info
  -pc             : show command list of program manage
  [APPID]         : show command list of APPID program
  -l              : show default log level of user program
  -l [level(0-8)] : set log level for all user program
  -pc -b          : show pc bbx info
  log             :show command list of log debug
```

```
# sendcmd 1   
[cspd]
sendcmd 1 :
  -p : show all PCB info
  -l : show log level of all PCB
  -l [level]: set log level of all PCB
  -task : show all tasks(threads)  info
  -socket  :show all socket(net local)  info
  -socket  :get/close
  -msg : show all PCB msg  info
  -timer : show all PCB timer  info
  -debug [FLAG]         : set/get 0(close) 1(open)
  -msgtimeout[ticks]    : set/get deal_message timeout
  -setdpr [udpwatch ip] : set udpwatch ip
  [PID Name] -p : show PCB detail info
  [PID Name] -l : show log level of PID module
  [PID Name] -l [level] : set log level of PID module
  [PID Name] ... : command of PID module
  -b : show bbx info
```

## APPID that can be controlled
```
/mnt # sendcmd -pc show                                                                                                                                                                 
Name             APPID  pid   inst  StartedbyName    State    EchoMsg                                                                                                                   
telnetd          61     448   0     cspd_misc        1        1                                                                                                                         
httpd            3      447   0     cspd_misc        1        1                                                                                                                         
gpon_omci        132    434   0     omci_mgr         1        1                                                                                                                         
vsftpd           0      433   0     fm_mgr           1        1                                                                                                                         
cspd             1      181   0     pc               1        0 
```

## cspd databases

```
sendcmd 1 DB all 
0               APPList
1               AccessDev
2               AclCfg
3               AttrInfo
4               BoardInfo
5               BrGrp
6               BrGrp2ndIP
7               BrportInfo
8               DBBase
9               DDNSClient
10              DDNSHostname
11              DDNSService
12              DHCP6SHostCfg
13              DHCP6SHostInfo
14              DHCPCComm
15              DHCPSBind
16              DHCPSComm
17              DHCPSHostCfg
18              DHCPSHostInfo
19              DHCPSOpts
20              DHCPSPool
21              DMSCfg
22              DNSDHCPHostsList
23              DNSHostsList
24              DNSSettings
25              DSSCfg
26              DSSInfo
27              DevAuthInfo
28              DevIPv6Ctrl
29              DevInfo
30              EthDscpToTciProduct
31              EthGlobalConfProduct
32              EthLanMatch
33              EthMVlanTranslationProduct
34              EthPortConfProduct
35              EthQueueConfProduct
36              EthRatelimitProduct
37              EthTcToCosProduct
38              EthVlanConfProduct
39              EthVlanEntryProduct
40              EthVlanFilterProduct
41              EthVlanTranslationProduct
42              EthVlanTransparentProduct
43              FTPServerCfg
44              FTPUser
45              FWALG
46              FWBase
47              FWCustom
48              FWCustom6
49              FWDMZ
50              FWDMZ6
51              FWIP
52              FWIP6
53              FWLevel
54              FWPM
55              FWPMAPP
56              FWPMDEV
57              FWPT
58              FWPURL
59              FWSC
60              FWURL
61              FalsifyDefend
62              GEMPORT
63              GPONCFG
64              HLTCtl
65              HLTInfo
66              HLTLanStatInfo
67              HistoryHLTInfo
68              HistoryHLTLanStatInfo
69              HostNameList
70              IGMPProxy
71              IGMPWan
72              IPV6PRoute
73              InterfaceInfo
74              L2BAvailIF
75              L2BBridge
76              L2BFilter
77              L2BMarking
78              L3Forwarding
79              L3Forwarding6
80              L3ForwardingRT
81              L3ForwardingRT6
82              LAND
83              LANInfo
84              Log
85              LoopbackEthConf
86              LoopbackGlobalConf
87              LoopbackVlanConf
88              MAC
89              MACUsed
90              MLDProxyCfg
91              MLDWan
92              McTunnel46
93              MirrorConf
94              MultiCastAbility
95              MultiCastGlobalConf
96              MultiCastMvlanConf
97              MultiCastPortConf
98              MultiCastSpecialGroup
99              OMCICFG                                                                                                                                                                 
100             OPTICAL                                                                                                                                                       
101             PINGDiag
102             PPPJumboCfg
103             PRoute
104             PdtInterface
105             PdtLDAR
106             PhyLinkInfo
107             PortBinding
108             PortControl
109             PortLocate
110             PortPriority
111             PrefixBanPort
112             PrefixCfg
113             PrefixIfDG
114             QOSBasic
115             QOSClassification
116             QOSPolicer
117             QOSQueue
118             QOSShaper
119             RIPConf
120             RIPIf
121             RIPngConf
122             RaCfg
123             RouteIFInfo
124             RouteSYSRT
125             SNTP
126             SrmCfg
127             TCONT
128             TCONTQUEUE
129             TCONTQUEUERATELIMIT
130             TUNNEL46CFG
131             TUNNEL64CFG
132             TelnetCfg
133             TimeSynInfo
134             Tr069Queue
135             UPnPCfg
136             UPnPPortMap
137             Upgrade
138             UserIF
139             UserInfo
140             VLAN
141             VLANDEF
142             WANC
143             WANCD
44             WANCIP
145             WANCIPOpts
146             WANCIPPrvData
147             WANCPPP
148             WANCPPPComm
149             WANCPPPStatus
150             WAND
151             WANDCommCfg
152             WLCInfo
```

## cspd DEVInfo table
```
# sendcmd 1 DB p DevInfo                                                                                                                                                           
<Tbl name="DevInfo" RowCount="1">                                                                                                                                                       
        <Row No="0">                                                                                                                                                                    
                <DM name="ManuFacturer" val="ZTE"/>                                                                                                                                     
                <DM name="ManuFacturerOui" val="08F606"/>                                                                                                                               
                <DM name="ModelName" val="F601"/>                                                                                                                                       
                <DM name="Description" val="HomeGateWay"/>
                <DM name="ProductClass" val="F601"/>
                <DM name="SerialNumber" val="XXXXXXXXXXXXXX"/>
                <DM name="HardwareVerTag" val=""/>
                <DM name="BootVer" val="V6.0.1P1T12"/>
                <DM name="HardwareVer" val="V6.0"/>
                <DM name="SoftwareVer" val="V6.0.2P1T12"/>
                <DM name="SpecVer" val="1.0"/> 
                <DM name="WiFiFirmwareVer" val=""/>
                <DM name="DSPFirmwareVer" val=""/>
                <DM name="ModelFirmwareVer" val=""/>
                <DM name="ProvisioningCode" val="TLCO.GRP2"/>
                <DM name="VerDate" val="2016-03-08 03:25:33"/>
                <DM name="CfgLable" val="CVP-A"/>
                <DM name="HostName" val="atadeviceXX:XX:XX:XX:XX:XX"/>
                <DM name="SaveFlag" val="1"/>
                <DM name="FirstUseDate" val="0001-01-01T00:00:00Z"/>
                <DM name="DomainName" val=""/> 
                <DM name="SoftwareVerExtent" val=""/>
                <DM name="ManuFacturerURL" val="http://www.zte.com"/>
                <DM name="DeviceURL" val="http://www.zte.com"/>
                <DM name="Contact" val=""/>
                <DM name="Location" val=""/>
                <DM name="DeviceSummary" val=""/>
                <DM name="VersionMode" val="5"/>
                <DM name="OnuMode" val="1"/>
                <DM name="ChinaUnicomType" val="07s"/>
        </Row>
</Tbl>
```

## Momentarily changing the software version
```
# sendcmd 1 DB set DevInfo 0 SoftwareVer V6.0.1P1T12

# cat /proc/csp/softVersion
```

## Enabling FTP server
```
sendcmd 1 DB set FTPServerCfg 0 FtpEnable 1
sendcmd 1 DB set FTPServerCfg 0 WanIfEnable 1
sendcmd 1 DB save
reboot
```