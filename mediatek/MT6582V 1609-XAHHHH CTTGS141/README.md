# Summary
| key           | value                                                                                                                                    |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------|
| SoC           | MT6582V 1609-XAHHHH CTTGS141                                                                                                             |
| Device        | Huawei Y3II (3G), MB sticker: `S96582AA1`                                                                                                |
| Software used | [brom-dump (spft-replay, payloads)](https://github.com/arzam16/empty-sixty-five), commit 459d03d325d09b898df6429d2efbf57324ecb600        |

# Regions
| File name  | Name | Memory address |
|------------|------|----------------|
| dump-1.bin | BROM | 0x0            |
| dump-2.bin | SRAM | 0x100000       |
| dump-3.bin | DA   | 0x200000       |

# Device ID
```
$ ./spft-replay.py -i
[2023-11-25 02:37:00,405] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-11-25 02:37:09,940] <INFO> Found device
[2023-11-25 02:37:09,948] <INFO> Handshake completed!
[2023-11-25 02:37:09,949] <INFO> HW code: 6582
[2023-11-25 02:37:09,950] <INFO> HW subcode: 8A00
[2023-11-25 02:37:09,950] <INFO> HW version: CA01
[2023-11-25 02:37:09,951] <INFO> SW version: 0001
[2023-11-25 02:37:09,951] <INFO> BROM version: 05
[2023-11-25 02:37:09,952] <INFO> ME ID: D0B106638FF175EF24EAE0DD82A22914
[2023-11-25 02:37:09,954] <INFO> Raw target config value: 00000000
[2023-11-25 02:37:09,954] <INFO> Secure boot: NO
[2023-11-25 02:37:09,954] <INFO> Serial link auth: NO
[2023-11-25 02:37:09,954] <INFO> Download agent auth: NO
[2023-11-25 02:37:09,955] <INFO> Closing device
```

# Dump log
```
$ ./spft-replay.py -p ../payloads/build/release/piggyback/mt6582-usb-dump.bin -pr
[2023-11-25 02:40:00,930] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-11-25 02:40:09,400] <INFO> Found device
[2023-11-25 02:40:09,408] <INFO> Handshake completed!
[2023-11-25 02:40:09,409] <INFO> Payload size 67584 bytes (0x00010800)
[2023-11-25 02:40:09,410] <REPLAY> HW code: 6582
[2023-11-25 02:40:09,410] <REPLAY> Identify
[2023-11-25 02:40:09,411] <REPLAY> HW subcode: 8A00
[2023-11-25 02:40:09,412] <REPLAY> HW version: CA01
[2023-11-25 02:40:09,412] <REPLAY> SW version: 0001
[2023-11-25 02:40:09,414] <REPLAY> 0x10206044: 00000380
[2023-11-25 02:40:09,414] <REPLAY> Initialize PMIC
[2023-11-25 02:40:09,414] <REPLAY> Disable watchdog
[2023-11-25 02:40:09,416] <REPLAY> Initialize RTC
[2023-11-25 02:40:09,416] <REPLAY> Identify software components
[2023-11-25 02:40:09,416] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-11-25 02:40:09,417] <REPLAY> ME ID: D0B106638FF175EF24EAE0DD82A22914
[2023-11-25 02:40:09,417] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-11-25 02:40:09,418] <REPLAY> Initialize external memory interface
[2023-11-25 02:40:09,418] <REPLAY> Send payload
[2023-11-25 02:40:09,420] <INFO> Uploaded 1024 out of 67584 bytes (1%)
[2023-11-25 02:40:09,488] <INFO> Uploaded 67584 out of 67584 bytes (100%)
[2023-11-25 02:40:09,488] <REPLAY> Received DA checksum: BADB
[2023-11-25 02:40:09,489] <REPLAY> Jump to payload
[2023-11-25 02:40:09,489] <REPLAY> Wait for remaining data
[2023-11-25 02:40:09,489] <INFO> Waiting for custom payload response
[2023-11-25 02:40:09,516] <INFO> Received HELLO sequence
[2023-11-25 02:40:09,516] <INFO> Reading 65536 bytes
[2023-11-25 02:40:09,655] <INFO> Saved to dump-1.bin
[2023-11-25 02:40:09,656] <INFO> Reading 65536 bytes
[2023-11-25 02:40:09,786] <INFO> Saved to dump-2.bin
[2023-11-25 02:40:09,786] <INFO> Reading 131072 bytes
[2023-11-25 02:40:10,092] <INFO> Saved to dump-3.bin
[2023-11-25 02:40:10,092] <INFO> Received GOODBYE sequence
[2023-11-25 02:40:10,093] <INFO> Closing device
```

# Dump procedure
1. Kill the preloader
2. Pull the battery
3. (`spft-replay` waits for a connection here)
4. Connect the USB cable
5. Wait till `spft-replay` finishes
6. Disconnect the USB cable
