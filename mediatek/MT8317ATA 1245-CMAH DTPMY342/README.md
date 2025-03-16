# Summary
| key           | value                                                                                                                                    |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------|
| SoC           | MT8317ATA 1245-CMAH DTPMY342                                                                                                             |
| Device        | Acer Iconia B1-A71                                                                                                                       |
| Software used | [brom-dump (spft-replay, payloads)](https://github.com/arzam16/empty-sixty-five), commit 06f9214db6f735a838ad030e6236319ba2a2e44b        |

# Regions
| File name  | Name | Memory address |
|------------|------|----------------|
| dump-1.bin | BROM | 0xFFFF0000     |
| dump-2.bin | SRAM | 0xF0000000     |
| dump-3.bin | DA   | 0xC2000000     |

# Device ID
```
$ ./spft-replay.py -i
[2023-12-09 02:39:41,690] <INFO> Init backend
[2023-12-09 02:39:41,698] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 02:39:56,322] <INFO> Found device
[2023-12-09 02:39:56,326] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 02:39:56,330] <INFO> Handshake completed!
[2023-12-09 02:39:56,332] <INFO> HW code: 6575
[2023-12-09 02:39:56,333] <INFO> HW subcode: 8B00
[2023-12-09 02:39:56,334] <INFO> HW version: CB00
[2023-12-09 02:39:56,334] <INFO> SW version: E201
[2023-12-09 02:39:56,335] <INFO> BROM version: 05
[2023-12-09 02:39:56,336] <INFO> ME ID: A8D5A0267E7D68C5FA057F7C51F26943
[2023-12-09 02:39:56,337] <INFO> Raw target config value: 00000000
[2023-12-09 02:39:56,337] <INFO> Secure boot: NO
[2023-12-09 02:39:56,337] <INFO> Serial link auth: NO
[2023-12-09 02:39:56,338] <INFO> Download agent auth: NO
[2023-12-09 02:39:56,338] <INFO> Stopping transport
[2023-12-09 02:39:58,224] <INFO> USB transport has stopped!
```

# Dump log
```
$ ./spft-replay.py -p ../payloads/build/release/piggyback/mt6577-usb-dump.bin -pr
[2023-12-09 02:40:38,161] <INFO> Init backend
[2023-12-09 02:40:38,168] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 02:40:47,012] <INFO> Found device
[2023-12-09 02:40:47,017] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 02:40:47,020] <INFO> Handshake completed!
[2023-12-09 02:40:47,020] <INFO> Payload size 139232 bytes (0x00021FE0)
[2023-12-09 02:40:47,022] <REPLAY> HW code: 6575
[2023-12-09 02:40:47,023] <REPLAY> Detected MT6575E2
[2023-12-09 02:40:47,023] <REPLAY> Identify
[2023-12-09 02:40:47,025] <REPLAY> HW subcode: 8B00
[2023-12-09 02:40:47,026] <REPLAY> HW version: CB00
[2023-12-09 02:40:47,026] <REPLAY> SW version: E201
[2023-12-09 02:40:47,026] <REPLAY> Initialize PMIC
[2023-12-09 02:40:47,034] <REPLAY> Disable watchdog
[2023-12-09 02:40:47,038] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 02:40:47,040] <REPLAY> TOPRGU register 0xC0000000 == 00000064
[2023-12-09 02:40:47,042] <REPLAY> TOPRGU register 0xC0000004 == 0000FFE0
[2023-12-09 02:40:47,044] <REPLAY> TOPRGU register 0xC0000008 == 00000000
[2023-12-09 02:40:47,045] <REPLAY> TOPRGU register 0xC000000C == 00000000
[2023-12-09 02:40:47,047] <REPLAY> TOPRGU register 0xC0000010 == 000007FF
[2023-12-09 02:40:47,049] <REPLAY> TOPRGU register 0xC0000014 == 00000000
[2023-12-09 02:40:47,051] <REPLAY> TOPRGU register 0xC0000018 == 00000000
[2023-12-09 02:40:47,051] <REPLAY> Initialize RTC
[2023-12-09 02:40:47,083] <REPLAY> Identify software components
[2023-12-09 02:40:47,085] <REPLAY> ME ID: A8D5A0267E7D68C5FA057F7C51F26943
[2023-12-09 02:40:47,087] <REPLAY> Raw target config value: 00000000
[2023-12-09 02:40:47,087] <REPLAY> Secure boot: NO
[2023-12-09 02:40:47,087] <REPLAY> Serial link auth: NO
[2023-12-09 02:40:47,088] <REPLAY> Download agent auth: NO
[2023-12-09 02:40:47,089] <REPLAY> BROM version: 05
[2023-12-09 02:40:47,089] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 02:40:47,090] <REPLAY> Initialize external memory interface
[2023-12-09 02:40:47,093] <REPLAY> EMI_GENA (0xC0003070) set to 00000002, was 00000000
[2023-12-09 02:40:47,093] <REPLAY> Send payload
[2023-12-09 02:40:47,097] <INFO> Uploaded 1024 out of 139232 bytes (0%)
[2023-12-09 02:40:47,248] <INFO> Uploaded 139232 out of 139232 bytes (100%)
[2023-12-09 02:40:47,252] <REPLAY> Received DA checksum: 5737
[2023-12-09 02:40:47,252] <REPLAY> Jump to payload
[2023-12-09 02:40:47,254] <REPLAY> Wait for remaining data
[2023-12-09 02:40:47,254] <INFO> Waiting for custom payload response
[2023-12-09 02:40:47,265] <INFO> Received HELLO sequence
[2023-12-09 02:40:47,265] <INFO> Reading 65536 bytes
[2023-12-09 02:40:47,448] <INFO> Saved to dump-1.bin
[2023-12-09 02:40:47,449] <INFO> Reading 65536 bytes
[2023-12-09 02:40:47,586] <INFO> Saved to dump-2.bin
[2023-12-09 02:40:47,587] <INFO> Reading 262144 bytes
[2023-12-09 02:40:48,308] <INFO> Saved to dump-3.bin
[2023-12-09 02:40:48,309] <INFO> Received GOODBYE sequence
[2023-12-09 02:40:48,309] <INFO> Stopping transport
[2023-12-09 02:40:52,385] <INFO> USB transport has stopped!
```

# Dump procedure
1. (`spft-replay` waits for a connection here)
2. Hold the Vol+ key
3. Connect the USB cable, release the key once device connects in BROM mode
4. Wait till `spft-replay` finishes
5. Disconnect the USB cable
6. Hit the Reset key in a small hole next to the Power key
