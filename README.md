# CBT035
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 035 is a Load Module library with useful programs in it.  *   FILE 035
//*                                                                 *   FILE 035
//*       Short explanation and note about load module CBT Tape     *   FILE 035
//*       files:  (This is a "technology update".)                  *   FILE 035
//*                                                                 *   FILE 035
//*           Way back in time, before the TSO XMIT (TRANSMIT)      *   FILE 035
//*           command became popular, in the ancient days of the    *   FILE 035
//*           pre-1990's, it was necessary to include separate      *   FILE 035
//*           load module libraries on the CBT Tape, because an     *   FILE 035
//*           IEBCOPY unload of a load module file with RECFM=U     *   FILE 035
//*           was not compatible with RECFM=FB, LRECL=80 card-image *   FILE 035
//*           files, that most source programs are formatted with.  *   FILE 035
//*           Therefore, on the tape, if we wanted to distribute    *   FILE 035
//*           load modules, we had to make a separate file for      *   FILE 035
//*           source code and a separate file for load modules.     *   FILE 035
//*                                                                 *   FILE 035
//*           But now, that a load module library can be put into   *   FILE 035
//*           TSO XMIT format, which is FB-80 card image format,    *   FILE 035
//*           load modules can be included in the same file where   *   FILE 035
//*           source code is distributed.  So this development has  *   FILE 035
//*           lessened the need for separate load module files on   *   FILE 035
//*           the CBT Tape.  Load module libraries can now exist    *   FILE 035
//*           on a "source code file" as a member, which is a real  *   FILE 035
//*           load library in TSO XMIT format (FB-80)!              *   FILE 035
//*                                                                 *   FILE 035
//*           Nevertheless, this load module file has been here     *   FILE 035
//*           on the tape, and it includes many varied programs     *   FILE 035
//*           from many sources, from time immemorial.  This        *   FILE 035
//*           file provides a convenient place from which to        *   FILE 035
//*           install many programs.  Therefore, I've decided that  *   FILE 035
//*           rather than reduce the size of this file or eliminate *   FILE 035
//*           it altogether, I'm actually going to expand it, even  *   FILE 035
//*           though some of its load modules can be found in       *   FILE 035
//*           other places and in other CBT Tape files.             *   FILE 035
//*                                                                 *   FILE 035
//*       The following is a list of most of the programs in this   *   FILE 035
//*       library, and where their original source code is.         *   FILE 035
//*                                                                 *   FILE 035
//*           SOURCE FILE           LOAD MODULE NAME                *   FILE 035
//*             002  SOURCE           CBT973 - uncompres tape files *   FILE 035
//*             006  SOURCE           CBTUPD - insert ./ ADD cards  *   FILE 035
//*                                            into this doc        *   FILE 035
//*             006  SOURCE           DOCFILE - cols 73-80 of this  *   FILE 035
//*                                            documentation        *   FILE 035
//*             018  DOCUMENTATION    TSUPDATE                      *   FILE 035
//*             044  SOURCE           ASMTOZAF - PL1/F ASMTOZAP     *   FILE 035
//*             044  SOURCE           ASMTOZAP - PL/1 OPTIMIZER     *   FILE 035
//*                                    good with PL/1 V1.3 or more  *   FILE 035
//*             046  SOURCE           PACKRAT, PACKRATU - dataset   *   FILE 035
//*                                    scratch/uncat on disk packs  *   FILE 035
//*             068  SOURCE           TSTVS - Console FB-80 editor  *   FILE 035
//*             093  SOURCE           OFFLOAD                       *   FILE 035
//*             093  SOURCE           PDSLOAD                       *   FILE 035
//*             094  SOURCE           DAF                           *   FILE 035
//*             102  SOURCE           TAPESC46 - Version 4.6 (64K)  *   FILE 035
//*             102  SOURCE           TAPESCAN - Version 5.2 (64K)  *   FILE 035
//*             112  SOURCE           VTOC                          *   FILE 035
//*             133  SOURCE           LOGTIME (time of this LOGON)  *   FILE 035
//*             133  SOURCE           LASTCLPA                      *   FILE 035
//*             134  SOURCE           HEL  (moved to FILE 135)      *   FILE 035
//*             134  SOURCE           REVIEW  (moved to FILE 135)   *   FILE 035
//*             134  SOURCE           ZAP  (moved to FILE 135)      *   FILE 035
//*             147  SOURCE           ARCHINIT  \\                  *   FILE 035
//*             147  SOURCE           ARCHIVER   >>  ARCHIVER       *   FILE 035
//*             147  SOURCE           ARCHPARS  //                  *   FILE 035
//*             182  SOURCE           PDS86 - PDS Vers 8.6 loadmod. *   FILE 035
//*                                    (Needs PANELS and MSGS to    *   FILE 035
//*                                    run in ISPMODE.  Will run    *   FILE 035
//*                                    in line mode as is.  Use     *   FILE 035
//*                                    XISPM keyword when invoking. *   FILE 035
//*                                    SEE FILE 182 FOR PANELS AND  *   FILE 035
//*                                    MESSAGES.                    *   FILE 035
//*             182  SOURCE           PDS86I - PDS 8.6 genned with  *   FILE 035
//*                                    European dates.              *   FILE 035
//*             182  SOURCE           PDSORIG - Old original PDS    *   FILE 035
//*                                    program from ancient times.  *   FILE 035
//*             183  SOURCE           FASTPATH - Quick ISPF updates *   FILE 035
//*             183  SOURCE           FASTP149 - FASTPATH previous  *   FILE 035
//*                                              release            *   FILE 035
//*             193  SOURCE           TCOPY - Tape copying utility  *   FILE 035
//*             200  SOURCE           WHATSNEW - in a load library  *   FILE 035
//*             218  SOURCE           VSAMMAPP                      *   FILE 035
//*             229  SOURCE           COPYFILE - copies SL tape fls *   FILE 035
//*             229  SOURCE           COPYSLNL - copies SL to NL    *   FILE 035
//*             229  SOURCE           COPYNLNL - copies NL to NL    *   FILE 035
//*             229  SOURCE           IGG019WD - with COPYFILE      *   FILE 035
//*             229  SOURCE           IGG019WE - with COPYFILE      *   FILE 035
//*             229  SOURCE           COPYMODS - souped up version  *   FILE 035
//*                                    with much extra capability   *   FILE 035
//*             229  SOURCE           CKIEBGEN (SBG version of      *   FILE 035
//*                                    Baldomero Castilla's QSAM    *   FILE 035
//*                                    GET-PUT file copy program)   *   FILE 035
//*             264  SOURCE           LOOK (see what's in storage)  *   FILE 035
//*                                    Latest version doesn't get   *   FILE 035
//*                                    user-key CSA, but it must    *   FILE 035
//*                                    run APF-authorized.          *   FILE 035
//*             264  SOURCE           LOOKN - 64-bit version of     *   FILE 035
//*                                           LOOK program. Must    *   FILE 035
//*                                           run APF-authorized.   *   FILE 035
//*             264  SOURCE           UKEYCSA (APF-authorized)      *   FILE 035
//*                                    (allow/not Key-8 CSA)        *   FILE 035
//*                                    (UKEYCSA Y is needed for     *   FILE 035
//*                                    the LOOK command to run,     *   FILE 035
//*                                    for z/OS 1.8 and higher.)    *   FILE 035
//*             266  SOURCE           SS0104 tape mapping program   *   FILE 035
//*                                    (used to determine footages) *   FILE 035
//*             294  SOURCE           VSAMADTL  VSAMANAL            *   FILE 035
//*             294  SOURCE           VSAMAGET  VSAMANAL            *   FILE 035
//*             294  SOURCE           VSAMAHLP  VSAMANAL            *   FILE 035
//*             294  SOURCE           VSAMANAL  VSAMANAL            *   FILE 035
//*             294  SOURCE           VSAMANDX  VSAMANAL            *   FILE 035
//*                                   Compiled w/PL/1 Optimizer 131 *   FILE 035
//*             294  SOURCE           VSAMSIZE  VSAMANAL            *   FILE 035
//*             296  SOURCE           BLKDISK BLK3380 BLK3390       *   FILE 035
//*             296  SOURCE           BLK3375 BLK9345 BLK3350       *   FILE 035
//*             296  SOURCE           DSAT                          *   FILE 035
//*             296  SOURCE           DVOL                          *   FILE 035
//*             296  SOURCE           COMPARE                       *   FILE 035
//*             296  SOURCE           COMPARE$ alias of COMPARE     *   FILE 035
//*             296  SOURCE           COMPAREB                      *   FILE 035
//*             296  no source        COMPAREC from Serena Inc.     *   FILE 035
//*                                      PDS interface to SUPERC    *   FILE 035
//*                    see member COMXMIT in File 182               *   FILE 035
//*             296  no source        COMPAREW from Serena Inc.     *   FILE 035
//*                                      PDS interface to COMPAREX  *   FILE 035
//*                    see member COMXMIT in File 182               *   FILE 035
//*             296  SOURCE           RELEASE                       *   FILE 035
//*             296  SOURCE           RESET                         *   FILE 035
//*             296  SOURCE           XEQ                           *   FILE 035
//*             299  SOURCE           TAPEMAP & TAPEMAPO            *   FILE 035
//*             300  SOURCE           CDSCB                         *   FILE 035
//*             300  SOURCE           CPSCB                         *   FILE 035
//*             300  SOURCE           DUSER    - Displays TSO users *   FILE 035
//*                                              logged on, with    *   FILE 035
//*                                              their asid.        *   FILE 035
//*             300  SOURCE           LASTIPL                       *   FILE 035
//*             300  SOURCE           LPSCB                         *   FILE 035
//*             316  SOURCE           LISPDS (really LISTPDS)       *   FILE 035
//*             316  SOURCE           TAPEL - used with COPYFILE    *   FILE 035
//*             357  SOURCE           PDSMATCH - Compare 2 PDS dirs *   FILE 035
//*             365  SOURCE           OSTAREDC - OSTARXMT error     *   FILE 035
//*                                     checking assembler program  *   FILE 035
//*             423  SOURCE           LISTHEAD - Display headers of *   FILE 035
//*                                              load modules. Plus *   FILE 035
//*                                              hex display of its *   FILE 035
//*                                              first 300 bytes.   *   FILE 035
//*             533  SOURCE           VTT2DISK - Real Tape to FB-80 *   FILE 035
//*                                              AWS format disk.   *   FILE 035
//*             533  SOURCE           VTT2TAPE - AWS format FB-80   *   FILE 035
//*                                              disk to Real Tape. *   FILE 035
//*             541  SOURCE           CCKDDUMP - Disk to cckd fmt   *   FILE 035
//*             541  SOURCE           CCKDLOAD - Load from cckd fmt *   FILE 035
//*             566  SOURCE           APFLIST  - list APF libraries *   FILE 035
//*             566  SOURCE           ZAPDSCB  - Full screen change *   FILE 035
//*                                              for VTOC entries   *   FILE 035
//*             690  SOURCE           XMDSMAIN - browse virtual     *   FILE 035
//*                                               storage           *   FILE 035
//*             731  SOURCE           CINMX    - change XMIT and    *   FILE 035
//*                                               RECEIVE settings  *   FILE 035
//*                                   DTEST    - display TSO TEST   *   FILE 035
//*                                               PARMLIB settings  *   FILE 035
//*                                   LOADTEST - batch program to   *   FILE 035
//*                                               change them       *   FILE 035
//*                                   INMXD    - display XMIT and   *   FILE 035
//*                                               RECEIVE settings  *   FILE 035
//*                                   ADIS     - display public     *   FILE 035
//*                                               (PARMLIB) TSO     *   FILE 035
//*                                               "auth tables"     *   FILE 035
//*                                   EESCB    - display current    *   FILE 035
//*                                               Broadcast Dataset *   FILE 035
//*                                               status, and more  *   FILE 035
//*                                   LOGOPTS  - flip on/off bits   *   FILE 035
//*                                               controlled by     *   FILE 035
//*                                               IKJTSOxx LOGON    *   FILE 035
//*                                               parameter         *   FILE 035
//*                                   RECONLIM - display or change  *   FILE 035
//*                                               TCAS RECONLIM     *   FILE 035
//*                                               value, on the fly *   FILE 035
//*                                   SHOWTCAS - display and format *   FILE 035
//*                                               TCAS control blk. *   FILE 035
//*                                               APF-authorized    *   FILE 035
//*                                               because data is   *   FILE 035
//*                                               fetch-protected   *   FILE 035
//*                                   SHOWTPVT - display and format *   FILE 035
//*                                               TPVT control blk. *   FILE 035
//*                                               Not documented by *   FILE 035
//*                                               IBM               *   FILE 035
//*                                   UCBDASD  - display real UCB   *   FILE 035
//*                        (File 873) ULUDASD     DASD info, cyls,  *   FILE 035
//*                                               etc. Not APF-auth *   FILE 035
//*                                   UCBTAPE  - display real UCB   *   FILE 035
//*                        (File 873) ULUTAPE     TAPE info, with   *   FILE 035
//*                                               pending mounts.   *   FILE 035
//*                                               Not APF-authorizd *   FILE 035
//*                                   USERMAX  - display or change  *   FILE 035
//*                                               TCAS USERMAX      *   FILE 035
//*                                               value, on the fly *   FILE 035
//*             792  SOURCE           DISKMAP  - map DASD volume    *   FILE 035
//*                                               EAV capable.      *   FILE 035
//*             797  SOURCE           TSUB     - Reload and change  *   FILE 035
//*                                   LLWA     - your TSO session's *   FILE 035
//*                                   LWATMGR  - "auth tables"      *   FILE 035
//*                                   LWATEDIT - edit auth tables   *   FILE 035
//*             816  SOURCE           BDMNNOTC - Change default #   *   FILE 035
//*                                              of Global Notices  *   FILE 035
//*                                              in SYS1.BRODCAST   *   FILE 035
//*                                              produced by        *   FILE 035
//*                                              ACCOUNT/SYNC.      *   FILE 035
//*             826  SOURCE           CNCLPG   - Make address space *   FILE 035
//*                                              cancelable or      *   FILE 035
//*                                              non-cancelable,    *   FILE 035
//*                                              non-swappable or   *   FILE 035
//*                                              swappable. BURN an *   FILE 035
//*                                              address space.     *   FILE 035
//*             846  SOURCE           ONLCLIP  - Change the volser  *   FILE 035
//*                                              of a disk pack,    *   FILE 035
//*                                              while it is online.*   FILE 035
//*                                              IPL text is not    *   FILE 035
//*                                              affected.          *   FILE 035
//*             949  SOURCE           PDSUR    - IEHMOVE substitute *   FILE 035
//*                                              good for sequenti- *   FILE 035
//*                                              alization of pds's *   FILE 035
//*             994  SOURCE           LISTMOD  - Hex Dump an entire *   FILE 035
//*                                              load module, or    *   FILE 035
//*                                              alternatively      *   FILE 035
//*                                              from its entry pt  *   FILE 035
//*                                              till the end.      *   FILE 035
//*                                              Display in hex     *   FILE 035
//*                                              75 bytes wide.     *   FILE 035
//*                                              This is more use-  *   FILE 035
//*                                              ful than LISTMODD. *   FILE 035
//*             994  SOURCE           LISTMODD - Hex Dump an entire *   FILE 035
//*                                              load module, or    *   FILE 035
//*                                              alternatively      *   FILE 035
//*                                              from its entry pt  *   FILE 035
//*                                              till the end.      *   FILE 035
//*                                              Display in decimal *   FILE 035
//*                                              112 bytes wide.    *   FILE 035
//*                                                                 *   FILE 035
```
