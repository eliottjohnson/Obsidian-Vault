
[Editor link](https://mermaid-js.github.io/mermaid-live-editor/edit#pako:eNqtVdtq20AQ_ZVBUEjAqSXLkmW9haSpS6u22KGB4petNJaWWrvuXto4If_ekVaRbw2lUD8IMzPnzO3s7qOXywK91CuZMGYpgH6GmzXCm8UlzK1wpoIZvJGqZgZgNruoa2dm91x35lez9FXW4WXBthlT31GBXK2WHYfG3HApIJOC_M_Wt4wLyKVSuGat-xc3FaBAVW5TCMKL0B9AVB2T3FrU_8oyqlzwraylzuUGodgMN1Aj01ZhjcJQaNSGhm3Cw5R3WIguaWNeoLEbMJVCdIk46gHkFVMsN6j4gytErigG4RuyuqsHmCjgJ1NbLkrgwqDQ3GxdxfOb95-oiPGF3xXRZAp834cMvwwtzN69nUH67Pfrk4APn-5af7jvn0RH-OgQv_M7eHQIj4_gEMSH-PgQ3_h7AhdBOzc0F6jlz3bQGs7ybU4qo_lJW1ZwzUmG7WQW88tsEQxHw_CcmCZuc8GOan8avKz6mD9OQ_4if7Kr9mQejiF5aV6OYHpMEB8TTF-aWEsw8g_n5b7zz8DyHLVOIVfcNF22YUEv9mssFSvoFHGhDVt30k6fA8PTU1FZtVPoH-Ep-K6aUY_-IEmIygoorGo02ehVUF-GTnJToq0tYRGIxHBteK6BcjVRc1K0ZpqOUC0VHTR_1FLHpx3onAk4IyLDN7R21zhqWrHv1hOMTrq5Ubzv5bIFNAXRSSURQdExE0Hc99NENvfWLWqzY_Y7z9XsXfZmfgnZdS-KXaUn2-h2GpyUtWDGqr6wfdJussn_riQ60kVfid2_SXekMARWFLyJYWu6zmuElVT79XQSGO-S0sXjriDNywZVNpcVMwRjUJEYaIcrhT8sinzbN_TcaXb3-Qp-WFa0ez5xX8n1mtctGS3_npdr0oyhSuDsIyNlcnZ-gHGovwxiKbyBVyM9Pryg9-uxAS09UmWNSy-lvwW9QEtvKZ4ojlkjF1uRe-mKrTUOPLtpnrRrzkhFdW_dMOGlj969l16Mg8nrMJlEiR-M42AcJOHA25I9ImsQh3EcJ-PpOJlMoqeB9yAlkQSvR9PxlJzTIJyM4sSfDDykNUiVuTe2fWrbLF9bgFEWn34DawozHg)

```mermaid
gantt

    title ESA Run

    dateFormat  HH-mm

    axisFormat %H:%M

    todayMarker on

  

    section Monday

  

    Gain correlation with energy: 13-30, 5h

  

    section Tuesday

  

    Gain correlation with energy: 13-30, 2h

    Tomoscope dp/p measurement: 15-30, 3h

  
  

    section Wednesday

    Setup three energies, characterization of the beam energy and varying intensity with RFKO: 14-00, 3h

    1000 MeV/u HIGH :14-00, 30m

    1000 MeV/u LOW :14-30, 30m

    750 MeV/u HIGH :15-00, 30m

    750 MeV/u LOW :15-30, 30m

    650 MeV/u HIGH : 16-00, 30m

    650 MeV/u LOW : 16-30, 30m

  

    Montrac movements (cycle through Diode and SRAMS1/2/3): 17-30, 210m

  

    1000 MeV/u High: 17-30, 30m

    1000 MeV/u Low: 18-00, 30m

  

    750 MeV/u High: 18-30, 30m

    750 MeV/u Low: 19-00, 30m

  

    650 MeV/u High: 19-30, 30m

    650 MeV/u Low: 20-00, 30m

    RP access: crit, 21-00, 1h

  

    Degrader installation : 21-00, 3h

  

    section Thursday

    Degrader installation: 00-00, 2h

  

    Long run during the night to accumulate statistics on the Renesas memory: 02-00, 6h

  

    Degrader scan (multiple accesses): 08-00, 12h

  

    section Friday

    Access to remove degrader: 06-00, 2h

    ESA Test: 08-00, 10h

    CHIMERA MD: 18-00, 6h

  

    RP access: crit, 19-30, 1h

  

    section Saturday

    CHIMERA MD: 00-00, 8h

    ESA Test: 08-00, 10h

    CHIMERA MD: 18-00, 6h

  

    RP access: crit, 15-00, 1h

  

    section Sunday

  

    CHIMERA MD / additional time for ESA Test: 00-00, 24h

  

    RFKO with signal generator a higher frequency: 08-00, 8h

    MWPC quad scan: 08-00, 8h

    Collimator plexiglas test (Natalia): 08-00, 8h

  

     RP access: crit, 15-00, 1h
```
