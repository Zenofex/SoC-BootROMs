# Summary
| key           | value                                                                                                                                    |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------|
| SoC           | MT8382V 1521-XAHHAH CTTBA531                                                                                                             |
| Device        | Lenovo A7-30                                                                                                                             |
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
[2023-11-25 03:05:41,098] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-11-25 03:05:51,101] <INFO> Found device
[2023-11-25 03:05:51,106] <INFO> Handshake completed!
[2023-11-25 03:05:51,106] <INFO> HW code: 6582
[2023-11-25 03:05:51,107] <INFO> HW subcode: 8A00
[2023-11-25 03:05:51,107] <INFO> HW version: CA01
[2023-11-25 03:05:51,108] <INFO> SW version: 0001
[2023-11-25 03:05:51,108] <INFO> BROM version: 05
[2023-11-25 03:05:51,109] <INFO> ME ID: B1F3A071E9696973393497AA1C323C2D
[2023-11-25 03:05:51,109] <INFO> Raw target config value: 00000000
[2023-11-25 03:05:51,109] <INFO> Secure boot: NO
[2023-11-25 03:05:51,109] <INFO> Serial link auth: NO
[2023-11-25 03:05:51,109] <INFO> Download agent auth: NO
[2023-11-25 03:05:51,110] <INFO> Closing device
```

# Dump log
```
$ ./spft-replay.py -p ../payloads/build/release/piggyback/mt6582-usb-dump.bin -pr
[2023-11-25 03:06:21,577] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-11-25 03:06:47,647] <INFO> Found device
[2023-11-25 03:06:47,651] <INFO> Handshake completed!
[2023-11-25 03:06:47,652] <INFO> Payload size 67584 bytes (0x00010800)
[2023-11-25 03:06:47,652] <REPLAY> HW code: 6582
[2023-11-25 03:06:47,652] <REPLAY> Identify
[2023-11-25 03:06:47,653] <REPLAY> HW subcode: 8A00
[2023-11-25 03:06:47,654] <REPLAY> HW version: CA01
[2023-11-25 03:06:47,654] <REPLAY> SW version: 0001
[2023-11-25 03:06:47,655] <REPLAY> 0x10206044: 00000380
[2023-11-25 03:06:47,655] <REPLAY> Initialize PMIC
[2023-11-25 03:06:47,655] <REPLAY> Disable watchdog
[2023-11-25 03:06:47,657] <REPLAY> Initialize RTC
[2023-11-25 03:06:47,657] <REPLAY> Identify software components
[2023-11-25 03:06:47,657] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-11-25 03:06:47,658] <REPLAY> ME ID: B1F3A071E9696973393497AA1C323C2D
[2023-11-25 03:06:47,658] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-11-25 03:06:47,658] <REPLAY> Initialize external memory interface
[2023-11-25 03:06:47,658] <REPLAY> Send payload
[2023-11-25 03:06:47,661] <INFO> Uploaded 1024 out of 67584 bytes (1%)
[2023-11-25 03:06:47,732] <INFO> Uploaded 67584 out of 67584 bytes (100%)
[2023-11-25 03:06:47,733] <REPLAY> Received DA checksum: BADB
[2023-11-25 03:06:47,733] <REPLAY> Jump to payload
[2023-11-25 03:06:47,733] <REPLAY> Wait for remaining data
[2023-11-25 03:06:47,734] <INFO> Waiting for custom payload response
[2023-11-25 03:06:47,760] <INFO> Received HELLO sequence
[2023-11-25 03:06:47,761] <INFO> Reading 65536 bytes
[2023-11-25 03:06:47,903] <INFO> Saved to dump-1.bin
[2023-11-25 03:06:47,904] <INFO> Reading 65536 bytes
[2023-11-25 03:06:48,066] <INFO> Saved to dump-2.bin
[2023-11-25 03:06:48,066] <INFO> Reading 131072 bytes
[2023-11-25 03:06:48,381] <INFO> Saved to dump-3.bin
[2023-11-25 03:06:48,382] <INFO> Received GOODBYE sequence
[2023-11-25 03:06:48,382] <INFO> Closing device
```

# Dump procedure
1. (`spft-replay` waits for a connection here)
2. Hold the Vol+ key
3. Connect the USB cable, release the key once device connects in BROM mode
4. Wait till `spft-replay` finishes
5. Disconnect the USB cable
6. Hold Power key for 10 seconds or reconnect the battery (requires unscrewing 2 philips head screws) to reset the device to its normal state
