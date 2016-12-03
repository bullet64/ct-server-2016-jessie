#Install hdparm

    apt-get install hdparm
Look into /dev/disk/by-uuid

    root@nas:/dev/disk/by-id# ls
    ata-HGST_HTE541010A9E680_JA1000CRGG3AXP
    ata-HGST_HTE541010A9E680_JA1000CRGG3AXP-part1
    ata-HGST_HTS541010A9E680_JA1006C0162UJN
    ata-HGST_HTS541010A9E680_JA1006C0162UJN-part1
Note HHD-ID from your RAID

    ata-HGST_HTE541010A9E680_JA1000CRGG3AXP
    ata-HGST_HTS541010A9E680_JA1006C0162UJN
Edit /etc/hdparm.conf and add these lines to the end of the file.

    #RAID md0 sleep after 20 Minutes (240*5=1200 seconds = 20 minutes)
    /dev/disk/by-id/ata-HGST_HTE541010A9E680_JA1000CRGG3AXP {
    #       mult_sect_io = 16
    #       write_cache = off
    #       dma = on
    spindown_time = 240
    }

    /dev/disk/by-id/ata-HGST_HTS541010A9E680_JA1006C0162UJN {
    #       mult_sect_io = 16
    #       write_cache = off
    #       dma = on
    spindown_time = 240
    }
Save the file and reboot your NAS.
