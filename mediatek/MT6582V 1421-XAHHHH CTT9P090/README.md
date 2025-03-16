# Summary
| key           | value                                                                                                                                    |
|---------------|------------------------------------------------------------------------------------------------------------------------------------------|
| SoC           | MT6582V 1421-XAHHHH CTT9P090                                                                                                             |
| Device        | Micromax A106                                                                                                                            |
| Software used | [brom-dump (spft-replay, payloads)](https://github.com/arzam16/empty-sixty-five), commit 06f9214db6f735a838ad030e6236319ba2a2e44b        |

# Regions
| File name  | Name | Memory address |
|------------|------|----------------|
| dump-1.bin | BROM | 0x0            |
| dump-2.bin | SRAM | 0x100000       |
| dump-3.bin | DA   | 0x200000       |

# Device ID
```
$ ./spft-replay.py -i
[2023-12-09 02:54:55,040] <INFO> Init backend
[2023-12-09 02:54:55,047] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 02:55:11,682] <INFO> Found device
[2023-12-09 02:55:11,687] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 02:55:11,690] <INFO> Handshake completed!
[2023-12-09 02:55:11,691] <INFO> HW code: 6582
[2023-12-09 02:55:11,692] <INFO> HW subcode: 8A00
[2023-12-09 02:55:11,693] <INFO> HW version: CA01
[2023-12-09 02:55:11,693] <INFO> SW version: 0001
[2023-12-09 02:55:11,693] <INFO> BROM version: 05
[2023-12-09 02:55:11,695] <INFO> ME ID: 63188F8203468B2F732D3402A4D77DCA
[2023-12-09 02:55:11,696] <INFO> Raw target config value: 00000000
[2023-12-09 02:55:11,696] <INFO> Secure boot: NO
[2023-12-09 02:55:11,696] <INFO> Serial link auth: NO
[2023-12-09 02:55:11,697] <INFO> Download agent auth: NO
[2023-12-09 02:55:11,697] <INFO> Stopping transport
[2023-12-09 02:55:13,620] <INFO> USB transport has stopped!
```

# Dump log
```
$ ./spft-replay.py -p ../payloads/build/release/piggyback/mt6582-usb-dump.bin -pr
[2023-12-09 02:55:21,247] <INFO> Init backend
[2023-12-09 02:55:21,254] <INFO> Waiting for device in BROM mode (0E8D:0003)
[2023-12-09 02:55:26,017] <INFO> Found device
[2023-12-09 02:55:26,023] <INFO> USB transport has successfully started! Waiting for further commands...
[2023-12-09 02:55:26,025] <INFO> Handshake completed!
[2023-12-09 02:55:26,026] <INFO> Payload size 67584 bytes (0x00010800)
[2023-12-09 02:55:26,027] <REPLAY> HW code: 6582
[2023-12-09 02:55:26,027] <REPLAY> Identify
[2023-12-09 02:55:26,028] <REPLAY> HW subcode: 8A00
[2023-12-09 02:55:26,029] <REPLAY> HW version: CA01
[2023-12-09 02:55:26,029] <REPLAY> SW version: 0001
[2023-12-09 02:55:26,030] <REPLAY> 0x10206044: 00000380
[2023-12-09 02:55:26,031] <REPLAY> Initialize PMIC
[2023-12-09 02:55:26,031] <REPLAY> Disable watchdog
[2023-12-09 02:55:26,033] <REPLAY> Initialize RTC
[2023-12-09 02:55:26,033] <REPLAY> Identify software components
[2023-12-09 02:55:26,034] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 02:55:26,035] <REPLAY> ME ID: 63188F8203468B2F732D3402A4D77DCA
[2023-12-09 02:55:26,036] <WARNING> Cannot get PRELOADER version in BROM mode
[2023-12-09 02:55:26,036] <REPLAY> Initialize external memory interface
[2023-12-09 02:55:26,036] <REPLAY> Send payload
[2023-12-09 02:55:26,039] <INFO> Uploaded 1024 out of 67584 bytes (1%)
[2023-12-09 02:55:26,112] <INFO> Uploaded 67584 out of 67584 bytes (100%)
[2023-12-09 02:55:26,113] <REPLAY> Received DA checksum: 24C5
[2023-12-09 02:55:26,113] <REPLAY> Jump to payload
[2023-12-09 02:55:26,114] <REPLAY> Wait for remaining data
[2023-12-09 02:55:26,114] <INFO> Waiting for custom payload response
[2023-12-09 02:55:26,141] <INFO> Received HELLO sequence
[2023-12-09 02:55:26,142] <INFO> Reading 65536 bytes
[2023-12-09 02:55:26,330] <INFO> Saved to dump-1.bin
[2023-12-09 02:55:26,331] <INFO> Reading 65536 bytes
[2023-12-09 02:55:26,511] <INFO> Saved to dump-2.bin
[2023-12-09 02:55:26,512] <INFO> Reading 131072 bytes
[2023-12-09 02:55:26,851] <INFO> Saved to dump-3.bin
[2023-12-09 02:55:26,852] <INFO> Received GOODBYE sequence
[2023-12-09 02:55:26,852] <INFO> Stopping transport
[2023-12-09 02:55:30,941] <INFO> USB transport has stopped!
```

# Dump procedure
1. Kill the preloader
2. Pull the battery
3. (`spft-replay` waits for a connection here)
4. Connect the USB cable
5. Wait till `spft-replay` finishes
6. Disconnect the USB cable
