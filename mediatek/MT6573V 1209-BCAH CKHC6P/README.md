# Summary
| key           | value                                                                                                                                    |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------|
| SoC           | MT6573V 1209-BCAH CKHC6P                                                                                                                 |
| Device        | Highscreen Yummy Duo                                                                                                                     |
| Software used | [brom-dump (spft-replay, payloads)](https://github.com/arzam16/empty-sixty-five), commit 06f9214db6f735a838ad030e6236319ba2a2e44b        |

# Regions
| File name  | Name | Memory address |
|------------|------|----------------|
| dump-1.bin | BROM | 0x48000000     |
| dump-2.bin | SRAM | 0x40000000     |
| dump-3.bin | DA   | 0x90005000     |

# Device ID
```
$ ./spft-replay.py -i
[2023-12-09 02:47:11,510] <INFO> Init backend
[2023-12-09 02:47:11,519] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 02:47:20,542] <INFO> Found device
[2023-12-09 02:47:20,547] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 02:47:20,550] <INFO> Handshake completed!
[2023-12-09 02:47:20,551] <INFO> HW code: 6573
[2023-12-09 02:47:20,554] <INFO> HW version: CA10
[2023-12-09 02:47:20,554] <INFO> SW version: CA01
[2023-12-09 02:47:20,555] <INFO> BROM version: 05
[2023-12-09 02:47:20,556] <INFO> ME ID: 24B06916DCD1670AF5C4CE6649F081A6
[2023-12-09 02:47:20,557] <INFO> Raw target config value: 00000000
[2023-12-09 02:47:20,558] <INFO> Secure boot: NO
[2023-12-09 02:47:20,558] <INFO> Serial link auth: NO
[2023-12-09 02:47:20,558] <INFO> Download agent auth: NO
[2023-12-09 02:47:20,559] <INFO> Stopping transport
[2023-12-09 02:47:22,512] <INFO> USB transport has stopped!
```

# Dump log
```
$ ./spft-replay.py -p ../payloads/build/release/piggyback/mt6577-usb-dump.bin -pr
[2023-12-09 02:48:28,474] <INFO> Init backend
[2023-12-09 02:48:28,481] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 02:48:51,096] <INFO> Found device
[2023-12-09 02:48:51,100] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 02:48:51,104] <INFO> Handshake completed!
[2023-12-09 02:48:51,104] <INFO> Payload size 92724 bytes (0x00016A34)
[2023-12-09 02:48:51,106] <REPLAY> HW code: 6573
[2023-12-09 02:48:51,106] <REPLAY> Identify
[2023-12-09 02:48:51,109] <REPLAY> HW version: CA10
[2023-12-09 02:48:51,109] <REPLAY> SW version: CA01
[2023-12-09 02:48:51,109] <REPLAY> Initialize PMIC
[2023-12-09 02:48:51,146] <REPLAY> Disable watchdog
[2023-12-09 02:48:51,148] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 02:48:51,148] <REPLAY> Initialize RTC
[2023-12-09 02:48:51,150] <REPLAY> RTC register 0x70014000 == 0007
[2023-12-09 02:48:51,152] <REPLAY> RTC register 0x70014050 == 7AD3
[2023-12-09 02:48:51,153] <REPLAY> RTC register 0x70014054 == BE09
[2023-12-09 02:48:51,177] <REPLAY> Identify software components
[2023-12-09 02:48:51,178] <REPLAY> ME ID: 24B06916DCD1670AF5C4CE6649F081A6
[2023-12-09 02:48:51,180] <REPLAY> Raw target config value: 00000000
[2023-12-09 02:48:51,180] <REPLAY> Secure boot: NO
[2023-12-09 02:48:51,181] <REPLAY> Serial link auth: NO
[2023-12-09 02:48:51,181] <REPLAY> Download agent auth: NO
[2023-12-09 02:48:51,182] <REPLAY> BROM version: 05
[2023-12-09 02:48:51,183] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 02:48:51,183] <REPLAY> Initialize external memory interface
[2023-12-09 02:48:51,186] <REPLAY> EMI_GENA (0x70000000) set to 00000002, was 3B731FFF
[2023-12-09 02:48:51,187] <REPLAY> Send payload
[2023-12-09 02:48:51,190] <INFO> Uploaded 1024 out of 92724 bytes (1%)
[2023-12-09 02:48:51,286] <INFO> Uploaded 92724 out of 92724 bytes (100%)
[2023-12-09 02:48:51,288] <REPLAY> Received DA checksum: 0692
[2023-12-09 02:48:51,288] <REPLAY> Jump to payload
[2023-12-09 02:48:51,289] <REPLAY> Wait for remaining data
[2023-12-09 02:48:51,289] <REPLAY> Waiting for device to send remaining data
[2023-12-09 02:48:51,292] <REPLAY> <- DA: (unknown) C0
[2023-12-09 02:48:51,293] <REPLAY> <- DA: (unknown) 03
[2023-12-09 02:48:51,294] <REPLAY> <- DA: (unknown) 02
[2023-12-09 02:48:51,294] <REPLAY> <- DA: (unknown) 83
[2023-12-09 02:48:51,294] <INFO> Waiting for custom payload response
[2023-12-09 02:48:51,295] <INFO> Received HELLO sequence
[2023-12-09 02:48:51,295] <INFO> Reading 65536 bytes
[2023-12-09 02:48:51,461] <INFO> Saved to dump-1.bin
[2023-12-09 02:48:51,462] <INFO> Reading 262144 bytes
[2023-12-09 02:48:51,994] <INFO> Saved to dump-2.bin
[2023-12-09 02:48:51,995] <INFO> Reading 110592 bytes
[2023-12-09 02:48:52,269] <INFO> Saved to dump-3.bin
[2023-12-09 02:48:52,269] <INFO> Received GOODBYE sequence
[2023-12-09 02:48:52,270] <INFO> Stopping transport
[2023-12-09 02:48:56,337] <INFO> USB transport has stopped!
```

# Dump procedure
1. Kill the preloader
2. Pull out the battery
3. (`spft-replay` waits for a connection here)
4. Connect the USB cable
5. Connect the battery
4. Wait till `spft-replay` finishes
5. Disconnect the USB cable
6. Pull out the battery
