# File Systems

## Most Common File Systems

- [FAT32](https://en.wikipedia.org/wiki/File_Allocation_Table#FAT32) (File Allocation Table)
    - Journaling file system: ✘
    - Checksum / ECC: ✘
    - Native for Windows. Read-write supported by Linux, MacOS.
- [exFAT](https://en.wikipedia.org/wiki/ExFAT) (Extensible File Allocation Table)
    - Journaling file system: ✘
    - Checksum / ECC: ✘
    - Native for Windows. Read-write supported by Linux, MacOS.
- [NTFS](https://en.wikipedia.org/wiki/NTFS) (New Technology File System)
    - Microsoft's proprietary
    - Journaling file system: ✅
    - Checksum / ECC: ✘
    - Native for Windows. Read-only for MacOS. Read-Write for Linux via [NTFS-3G](https://en.wikipedia.org/wiki/NTFS-3G).
- [HFS+](https://en.wikipedia.org/wiki/HFS_Plus) (Hierarchical File System, a.k.a., Mac OS Extended)
    - Journaling file system: ✅
    - Checksum / ECC: ✘
    - Native for MacOS.
- [APFS](https://en.wikipedia.org/wiki/Apple_File_System) (Apple File System)
    - Apple's proprietary
    - Optimized for SSDs
    - Redirect-on-write (ROW): ✅
    - Checksum / ECC: ✔ Only for metadata, not for user data.
    - Native for MacOS.
- [ext4](https://en.wikipedia.org/wiki/Ext4) (Extended File System 4)
    - Checksum / ECC: ✔ Only for metadata, not for user data.
    - Native for Linux.
- [Btrfs](https://en.wikipedia.org/wiki/Btrfs) (B-tree File System, a.k.a, Better FS)
    - Checksum / ECC: ✅
    - Copy-on-write (COW): ✅  (Atomic Write)
    - Native for Linux.


## Distributed File System

- [GFS](https://en.wikipedia.org/wiki/Google_File_System) (Google File System)
- [Hadoop](https://en.wikipedia.org/wiki/Apache_Hadoop) (Apache Hadoop)
