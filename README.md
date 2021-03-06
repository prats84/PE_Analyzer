###### PE Analyzer ######
This script will extract static details from a valid PE
  and print them out.  It is offered in single and multiprocessing flavors.
Items analyzed:
  -Hashes
  -Import, Exports and Import hash
  -Static details such as compile time and version information
  -Fuzzy Hashes for PE, Imports and Sections
 -Custom YARA signatures as well as included crypto constant sigs
  -Cleartext and XOR encoded strings of interest
  -Cleartext and XOR [ single byte, WORD and DWORD] encoded PE's embedded within sample
  -Common Shellcode Techniques
  Requires path to a file to be analyzed like:
    PE_Analyzer.py foo.exe
  
 Example Output From a ZXShell Sample
 # MD5              : 7d31919503f3570d46e410919993b034
 # SHA1             : e036c49c79fccb2378c3db6eefb3073d3aeaa3f1
 # SHA256           : 5d2a4cde9fa7c2fdbf39b2e2ffd23378d0c50701a3095d1e91e3cf922d7b0b16
 # SSDEEP           : 24576:2B/IL2+Xk6j8Rd+hK2lGk3aFr5zUKgTVIGiuV2WqOD:S/IL2+U6cd+IKAUKQnZqOD
 # Import Hash      : 360ba640f500b4bb8584bb9ca4cec88b
 # Fuzzy Import Hash: 12:mdFN9MVg7O1dz9u6dxPFZ4mcyVZSjAgZGCZB:E91a1FV3PFZ4mcAZ8/B
 # File Size        : 950368
 # Major Version    : 5
 # Minor Version    : 1
 # Compiletime UTC  : 12/24/2014 09:09:53
 # Compiletime EPOCH: 1419412193
 # MIME Type        : application/x-dosexec
 # File Magic       : PE32 executable (DLL) (console) Intel 80386, for MS Windows
 # PE Sections      :
   Name  : .text
   MD5   : 163c64599d79322c596724b07b8b1c3e
   Size  : 261120
   SSDEEP: 3::
 
   Name  : .rdata
   MD5   : 882510633f1de7ca620f954d9d938b2b
   Size  : 67072
   SSDEEP: 1536:/Zu0Jb6Kz5k8vxqcg20aF4w2pi0KfZ9R0+:jJb6wk85qcg20a2w2phKp0+
 
   Name  : .data
   MD5   : a4d961e6ca1372e2db7394a9a9f313af
   Size  : 230400
   SSDEEP: 3072:yMao2l9eaGjiSTXzOoZLWBUp0Aw0djaps7WN6Of7+P95/9Yik3Uiw1oDrW:yZo2l9YxOolWcjapmzOjK5FYg11oDq
 
   Name  : .zh0
   MD5   : 18c2f27a8641da65a8936242bbce2ac7
   Size  : 268800
   SSDEEP: 3072:7aps7WN6Of7+P95/9Yik3Uiw1oDr3Xj+LT1R7gZrlfRbi35tybCVNEcl0:7apmzOjK5FYg11oDTT8zUpfRb6tGwNx0
 
   Name  : .zh1
   MD5   : c7fd2160012526aa7708d5a3784cd929
   Size  : 104448
   SSDEEP: 3072:uHFRf5BEvGjxNgT0qjV2HpVzGM/LMT6AXGoKbiuo:ulRf5BaG1SjWpf9AXGiuo
 
   Name  : .reloc
   MD5   : cebfde9dc81a4587832ef23054c66282
   Size  : 15360
   SSDEEP: 384:VRLKDd2PTcuSG7HPj0539TDJxidRMQ1u5zzQ:VRLMd2fjjS3VDJgGQ1uzc
 
   Name  : .rsrc
   MD5   : 174d54af2191173b9759cd8a003f9194
   Size  : 1024
   SSDEEP: 24:r6CUJvFarSDvLKA17t6pii0CLVwFXpw5xdNDXC402o0Mn:rgvFa0GA1EiPqmFpsdhXC40J0M
# Compiled Language    : LANG_ENGLISH
# Compiled Sub-Language: SUBLANG_ENGLISH_US
 
 # Imports:
   WININET.dll!InternetOpenUrlA
   MPR.dll!WNetCloseEnum
   KERNEL32.dll!GetVersion
   KERNEL32.dll!GetVersionExA
   KERNEL32.dll!FormatMessageA
   ADVAPI32.dll!GetServiceDisplayNameA
   GDI32.dll!CreateCompatibleBitmap
   SHELL32.dll!SHFileOperationA
   USER32.dll!GetClassNameA
   PSAPI.DLL!EnumProcesses
   WS2_32.dll!WSAIoctl
   NETAPI32.dll!NetUserEnum
   DNSAPI.dll!DnsRecordListFree
   SHLWAPI.dll!PathMatchSpecA
   IPHLPAPI.DLL!GetAdaptersInfo
   AVICAP32.dll!capGetDriverDescriptionA
   WTSAPI32.dll!WTSFreeMemory
   USERENV.dll!CreateEnvironmentBlock
   ole32.dll!CoTaskMemFree
   KERNEL32.dll!GetModuleFileNameW
   KERNEL32.dll!GetModuleHandleA
   KERNEL32.dll!LoadLibraryA
   KERNEL32.dll!LocalAlloc
   KERNEL32.dll!LocalFree
   KERNEL32.dll!GetModuleFileNameA
   KERNEL32.dll!ExitProcess
 # Exports:
   DebugHelp
   DllMain
   HideLibrary
   Install
   RemoteDiskXXXXX
   ShellMain
   ShellMainThread
   UnInstall
   doAction_CreateThread
   zxFunction001
   zxFunction002
 #  Scanning with YARA signatures
   Loaded ruleset: crypto_signatures.yar
   Sample matched YARA rule: CRC32_poly_Constant
   Sample matched YARA rule: CRC32_table
   Sample matched YARA rule: MD5_Constants
   Sample matched YARA rule: BASE64_table
 # Cleartext Interesting Strings
   String found at offset 0x7a94b --> amd64\amd64\msfsrvc.pdb
   String found at offset 0x83bfb --> x86\i386\msfsrvc.pdb
   String found at offset 0x425ad --> 61.8.8.13
   String found at offset 0x425b7 --> 61.8.9.28
   String found at offset 0x42936 --> 61.8.8.13
   String found at offset 0x42940 --> 61.8.9.28
   String found at offset 0x44c10 --> 127.0.0.1
   String found at offset 0x47a37 --> 1.1.1.1
   String found at offset 0x47a63 --> 1.1.1.1
   String found at offset 0x48774 --> 127.0.0.1
   String found at offset 0x489dc --> 127.0.0.1
   String found at offset 0x40f18 --> ntdll.dll
   String found at offset 0x412ed --> test.exe
   String found at offset 0x41300 --> test.exe
   String found at offset 0x4131d --> lsass.exe
   String found at offset 0x41343 --> test.exe
   String found at offset 0x41352 --> test.exe
   String found at offset 0x4139b --> test.exe
   String found at offset 0x413aa --> test.exe
   String found at offset 0x42274 --> KERNEL32.dll
   String found at offset 0x42360 --> Dnsapi.dll
   String found at offset 0x423dc --> \cmd.exe
   String found at offset 0x42b17 --> cmd.exe
   String found at offset 0x42b46 --> cmd.exe
   String found at offset 0x42d03 --> \x.exe
   String found at offset 0x42d0a --> x.exe
   String found at offset 0x42d29 --> x.exe
   String found at offset 0x42d31 --> \x.exe
   String found at offset 0x43e14 --> rundll32.exe
   String found at offset 0x4416a --> \windows\update.exe
   String found at offset 0x4419e --> update.exe
   String found at offset 0x44b52 --> \Windows\System32\rpcss.dll
   String found at offset 0x44b95 --> Defender\MpSvc.dll
   String found at offset 0x44bd4 --> update.exe
   String found at offset 0x44c1f --> cmd.exe
   String found at offset 0x44df0 --> kernel32.dll
   String found at offset 0x44e30 --> PCHunter64.exe
   String found at offset 0x44e40 --> taskmgr.exe
   String found at offset 0x45315 --> \a.exe
   String found at offset 0x45eb4 --> Windows\regedit.exe
   String found at offset 0x45f49 --> s\expand.exe
   String found at offset 0x45f75 --> s\expand.exe
   String found at offset 0x4606c --> \rundll32.exe
   String found at offset 0x4610d --> \a.exe
   String found at offset 0x46116 --> \b.exe
   String found at offset 0x4611e --> b.exe
   String found at offset 0x4628d --> \System32\svchost.exe
   String found at offset 0x47060 --> V3Lite.exe
   String found at offset 0x4706c --> ASDSvc.exe
   String found at offset 0x470ac --> AvastUI.exe
   String found at offset 0x470b8 --> AvastSvc.exe
   String found at offset 0x470c8 --> afwServ.exe
   String found at offset 0x470d4 --> Smc.exe
   String found at offset 0x470dc --> ccSvcHst.exe
   String found at offset 0x470ec --> msseces.exe
   String found at offset 0x470f8 --> NisSrv.exe
   String found at offset 0x47104 --> MsMpEng.exe
   String found at offset 0x47110 --> avp.exe
   String found at offset 0x474e4 --> cab.exe
   String found at offset 0x474ff --> s.exe
   String found at offset 0x47821 --> s\rundll32.exe
   String found at offset 0x47878 --> \system32\rundll32.exe
   String found at offset 0x47890 --> \SysWOW64\rundll32.exe
   String found at offset 0x478b5 --> wireshark.exe
   String found at offset 0x478d1 --> netman.exe
   String found at offset 0x478dc --> cmd.exe
   String found at offset 0x482c6 --> \a.exe
   String found at offset 0x48783 --> cmd.exe
   String found at offset 0x48c34 --> Wtsapi32.dll
   String found at offset 0x49012 --> \xyz.dll
   String found at offset 0x49046 --> xyz.dll
   String found at offset 0x49083 --> \xyz.dll
   String found at offset 0x490a2 --> x.dll
   String found at offset 0x4a620 --> shell32.dll
   String found at offset 0x503b6 --> Msfsrvc.dll
   String found at offset 0x515a4 --> sekurlsaX86.exe
   String found at offset 0x6167c --> sekurlsaX64.exe
   String found at offset 0x79810 --> services.exe
   String found at offset 0x79820 --> svchost.exe
   String found at offset 0x79970 --> taskmgr.exe
   String found at offset 0x79980 --> PCHunter64.exe
   String found at offset 0x79f60 --> netstat.exe
   String found at offset 0x79f70 --> ipconfig.exe
   String found at offset 0x7a280 --> ekrn.exe
   String found at offset 0x7a290 --> egui.exe
   String found at offset 0x7ae00 --> winlogon.exe
   String found at offset 0x7ae14 --> csrss.exe
   String found at offset 0x7ae28 --> services.exe
   String found at offset 0x7ae3c --> lsass.exe
   String found at offset 0x7ae50 --> svchost.exe
   String found at offset 0x7ae64 --> wininit.exe
   String found at offset 0x7ae78 --> smss.exe
   String found at offset 0x7ae8c --> rundll32.exe
   String found at offset 0x7aea0 --> iexplore.exe
   String found at offset 0x7aeb4 --> expand.exe
   String found at offset 0x7aec8 --> update.exe
   String found at offset 0x7aedc --> consent.exe
   String found at offset 0x7c942 --> ntoskrnl.exe
   String found at offset 0x82d18 --> PCHunter64.exe
   String found at offset 0x82d28 --> taskmgr.exe
   String found at offset 0x82e78 --> svchost.exe
   String found at offset 0x82e88 --> services.exe
   String found at offset 0x83798 --> egui.exe
   String found at offset 0x837a8 --> ekrn.exe
   String found at offset 0x83de8 --> winlogon.exe
   String found at offset 0x83dfc --> csrss.exe
   String found at offset 0x83e10 --> services.exe
   String found at offset 0x83e24 --> lsass.exe
   String found at offset 0x83e38 --> svchost.exe
   String found at offset 0x83e4c --> wininit.exe
   String found at offset 0x83e60 --> smss.exe
   String found at offset 0x83e74 --> rundll32.exe
   String found at offset 0x83e88 --> iexplore.exe
   String found at offset 0x83e9c --> expand.exe
   String found at offset 0x83eb0 --> update.exe
   String found at offset 0x83ec4 --> consent.exe
   String found at offset 0x853e4 --> ntoskrnl.exe
   String found at offset 0x85460 --> HAL.dll
   String found at offset 0x872e8 --> winlogon.exe
   String found at offset 0x87400 --> LogonUI.exe
   String found at offset 0x87480 --> explorer.exe
   String found at offset 0x8758d --> s\rundll32.exe
   String found at offset 0xca52a --> user32.dll
   String found at offset 0xcb630 --> WS2_32.dll
   String found at offset 0xcc88d --> KERNEL32.dll
   String found at offset 0xcda30 --> hUSER32.dll
   String found at offset 0xd0630 --> DgADVAPI32.dll
   String found at offset 0xd3542 --> GDI32.dll
   String found at offset 0xd3a64 --> USERENV.dll
   String found at offset 0xd40d3 --> WTSAPI32.dll
   String found at offset 0xd4283 --> DNSAPI.dll
   String found at offset 0xd4445 --> SHELL32.dll
   String found at offset 0xd7b11 --> NETAPI32.dll
   String found at offset 0xd8935 --> AVICAP32.dll
   String found at offset 0xdbbdf --> MPR.dll
   String found at offset 0xdc60b --> ole32.dll
   String found at offset 0xdc6e6 --> SHLWAPI.dll
   String found at offset 0xde364 --> WININET.dll
 # XOR Encdoded Interesting Strings
   String found at offset 0x418d1 with XOR Key [0xe] --> kw@ock.jk
   String found at offset 0x458ac with XOR Key [0xe] --> bow@ock.ha
   String found at offset 0x458e5 with XOR Key [0xe] --> kw@ock.ha
   String found at offset 0x43bfa with XOR Key [0x10] --> ud@qcc0000000000000000000--.wud
   String found at offset 0x447c9 with XOR Key [0x10] --> ud@qcc0000000000000000000--.wud
   String found at offset 0xe7ca4 with XOR Key [0x12] --> 8.8.8.8
   String found at offset 0xe7cac with XOR Key [0x12] --> 193.0.14.129
   String found at offset 0xe7d74 with XOR Key [0x12] --> msecxepsrv.dll
   String found at offset 0x4cf55 with XOR Key [0x35] --> 555.5.5.554
   String found at offset 0x413e9 with XOR Key [0x62] --> bbb8bbb@bbb.bbb
   String found at offset 0x73aa8 with XOR Key [0x85] --> 127.0.0.2
 # Possible Domain Names
   Domain found at offset 0x44060 with XOR key [0x0]: www.222.com
   Domain found at offset 0x4406c with XOR key [0x0]: www.333.com
   Domain found at offset 0x44078 with XOR key [0x0]: www.555.com
   Domain found at offset 0x44185 with XOR key [0x0]: www.facebook.com
   Domain found at offset 0x4591f with XOR key [0x0]: www.google.com
   Domain found at offset 0x474dc with XOR key [0x0]: makecab.ca
   Domain found at offset 0x47509 with XOR key [0x0]: makecab.ca
   Domain found at offset 0x487b8 with XOR key [0x0]: crl.microsoft.com
   Domain found at offset 0x48835 with XOR key [0x0]: time.microsoft.com
   Domain found at offset 0x488ee with XOR key [0x0]: time.microsoft.com
   Domain found at offset 0x7d3fd with XOR key [0x0]: cs-g2-crl.thawte.com
   Domain found at offset 0x7d485 with XOR key [0x0]: ocsp.thawte.com
   Domain found at offset 0x7d85d with XOR key [0x0]: crl.thawte.com
   Domain found at offset 0x7d8ae with XOR key [0x0]: ocsp.thawte.com
   Domain found at offset 0x7dd87 with XOR key [0x0]: crl.microsoft.com
   Domain found at offset 0xe79fc with XOR key [0x0]: schemas.microsoft.com
   Domain found at offset 0xe7a3a with XOR key [0x0]: schemas.microsoft.com
   Domain found at offset 0x4bfe8 with XOR key [0x3]: psbmjpk.nl
   Domain found at offset 0x43c39 with XOR key [0x6]: vguuqitb.us
   Domain found at offset 0x44808 with XOR key [0x6]: vguuqitb.us
   Domain found at offset 0x416aa with XOR key [0xe]: kmghgkj.ca
   Domain found at offset 0x416d1 with XOR key [0xe]: obb.zfk.ca
   Domain found at offset 0x43552 with XOR key [0x4a]: bo.go.go.jo.po.po.co
   Domain found at offset 0x44506 with XOR key [0x4a]: bo.go.go.jo.po.po.co
   Domain found at offset 0xe7c0e with XOR key [0x85]: api7.mcafee.01o.us
   Domain found at offset 0x36786 with XOR key [0x9a]: irMaees.de
 # Carving Additional PEs
   Found embedded PE at offset 0x746e0 with XOR key [0x0] and MD5 of c280772220c7548b725f677415020794
   Found embedded PE at offset 0x7e1d8 with XOR key [0x0] and MD5 of fb95be894eab216d492da4fd860c6faa
 # Looking for Common Shellcode Techniques
 
