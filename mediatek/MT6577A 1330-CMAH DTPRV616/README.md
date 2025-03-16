# Summary
| key           | value                                                                                                                                    |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------|
| SoC           | MT6577A 1330-CMAH DTPRV616                                                                                                               |
| Device        | MTS 975 (original name in cyrillic script: МТС 975)                                                                                  |
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
[2023-12-09 03:06:36,695] <INFO> Init backend
[2023-12-09 03:06:36,701] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 03:06:43,238] <INFO> Found device
[2023-12-09 03:06:43,244] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 03:06:43,246] <INFO> Handshake completed!
[2023-12-09 03:06:43,247] <INFO> HW code: 6575
[2023-12-09 03:06:43,249] <INFO> HW subcode: 8B00
[2023-12-09 03:06:43,249] <INFO> HW version: CB00
[2023-12-09 03:06:43,249] <INFO> SW version: E201
[2023-12-09 03:06:43,250] <INFO> BROM version: 05
[2023-12-09 03:06:43,251] <INFO> ME ID: 1AD96C3679768FCACAF78A6C92A7A53D
[2023-12-09 03:06:43,252] <INFO> Raw target config value: 00000000
[2023-12-09 03:06:43,252] <INFO> Secure boot: NO
[2023-12-09 03:06:43,253] <INFO> Serial link auth: NO
[2023-12-09 03:06:43,253] <INFO> Download agent auth: NO
[2023-12-09 03:06:43,253] <INFO> Stopping transport
[2023-12-09 03:06:45,176] <INFO> USB transport has stopped!
```

# Dump log
```
$ ./spft-replay.py -p ../payloads/build/release/piggyback/mt6577-usb-dump.bin -pr
[2023-12-09 03:06:57,297] <INFO> Init backend
[2023-12-09 03:06:57,304] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 03:07:07,047] <INFO> Found device
[2023-12-09 03:07:07,053] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 03:07:07,055] <INFO> Handshake completed!
[2023-12-09 03:07:07,056] <INFO> Payload size 139232 bytes (0x00021FE0)
[2023-12-09 03:07:07,056] <REPLAY> HW code: 6575
[2023-12-09 03:07:07,058] <REPLAY> Detected MT6575E2
[2023-12-09 03:07:07,058] <REPLAY> Identify
[2023-12-09 03:07:07,060] <REPLAY> HW subcode: 8B00
[2023-12-09 03:07:07,060] <REPLAY> HW version: CB00
[2023-12-09 03:07:07,060] <REPLAY> SW version: E201
[2023-12-09 03:07:07,061] <REPLAY> Initialize PMIC
[2023-12-09 03:07:07,068] <REPLAY> Disable watchdog
[2023-12-09 03:07:07,072] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 03:07:07,074] <REPLAY> TOPRGU register 0xC0000000 == 00000064
[2023-12-09 03:07:07,076] <REPLAY> TOPRGU register 0xC0000004 == 0000FFE0
[2023-12-09 03:07:07,077] <REPLAY> TOPRGU register 0xC0000008 == 00000000
[2023-12-09 03:07:07,079] <REPLAY> TOPRGU register 0xC000000C == 00000000
[2023-12-09 03:07:07,081] <REPLAY> TOPRGU register 0xC0000010 == 000007FF
[2023-12-09 03:07:07,083] <REPLAY> TOPRGU register 0xC0000014 == 00000000
[2023-12-09 03:07:07,085] <REPLAY> TOPRGU register 0xC0000018 == 00000000
[2023-12-09 03:07:07,085] <REPLAY> Initialize RTC
[2023-12-09 03:07:07,113] <REPLAY> Identify software components
[2023-12-09 03:07:07,114] <REPLAY> ME ID: 1AD96C3679768FCACAF78A6C92A7A53D
[2023-12-09 03:07:07,116] <REPLAY> Raw target config value: 00000000
[2023-12-09 03:07:07,117] <REPLAY> Secure boot: NO
[2023-12-09 03:07:07,117] <REPLAY> Serial link auth: NO
[2023-12-09 03:07:07,117] <REPLAY> Download agent auth: NO
[2023-12-09 03:07:07,118] <REPLAY> BROM version: 05
[2023-12-09 03:07:07,119] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 03:07:07,120] <REPLAY> Initialize external memory interface
[2023-12-09 03:07:07,123] <REPLAY> EMI_GENA (0xC0003070) set to 00000002, was 00000000
[2023-12-09 03:07:07,123] <REPLAY> Send payload
[2023-12-09 03:07:07,126] <INFO> Uploaded 1024 out of 139232 bytes (0%)
[2023-12-09 03:07:07,276] <INFO> Uploaded 139232 out of 139232 bytes (100%)
[2023-12-09 03:07:07,279] <REPLAY> Received DA checksum: 5737
[2023-12-09 03:07:07,280] <REPLAY> Jump to payload
[2023-12-09 03:07:07,281] <REPLAY> Wait for remaining data
[2023-12-09 03:07:07,281] <INFO> Waiting for custom payload response
[2023-12-09 03:07:07,292] <INFO> Received HELLO sequence
[2023-12-09 03:07:07,292] <INFO> Reading 65536 bytes
[2023-12-09 03:07:07,476] <INFO> Saved to dump-1.bin
[2023-12-09 03:07:07,477] <INFO> Reading 65536 bytes
[2023-12-09 03:07:07,654] <INFO> Saved to dump-2.bin
[2023-12-09 03:07:07,654] <INFO> Reading 262144 bytes
[2023-12-09 03:07:08,363] <INFO> Saved to dump-3.bin
[2023-12-09 03:07:08,364] <INFO> Received GOODBYE sequence
[2023-12-09 03:07:08,364] <INFO> Stopping transport
[2023-12-09 03:07:12,449] <INFO> USB transport has stopped!
```

# Dump procedure
1. Kill the preloader
2. Reconnect the battery
3. (`spft-replay` waits for a connection here)
4. Connect the USB cable
5. Wait till `spft-replay` finishes
6. Disconnect the USB cable
7. Pull out the battery
