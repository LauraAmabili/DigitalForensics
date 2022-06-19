# SSD
## Introduction 
In order to write on nand, you need to blank the block completely.
FTL (flash translation layer) chips are devices used to optimize the access to the SSD
Nand based flash memories chips used as mass storage, they became popular
nand chips have a limited lifespan, you can reprogram the chips a limited number of times
they have to be completed cleaned and rewrite, you cannot split the bits
Flt filters everything and makes the computer believe there is a rotational drives behind
### Flt
hw/sw combination that sits between ATA channel and memory chips

**Write caching**  a lot of caches, it is important because we power down clear the cache 
**Trimming**: 
preemptive blanking of erased blocks marked for trimming by the os. 
most important-> write we need to black and write ( black need time) so write takes more time than reading
if this block is not in use anymore, why do I have leave it written so that when i have to overwrite i have to bleak it first ? if i have a list of block that i can overwritten, when i have nothing to do i go the the list and clean it
the drive have a list of blocks that i need tofree and goes to them and black it   
trimming: act of trimming powered by the OS that gives the list of blocks

it would have better if the drive know which block are free and go to free them itsef-> **garbage collector**
since everytime we write on a cell we are using it ( decreasing it life), the less we write the better so we do compression 
balance how fast we can comopress things
**bad block handling**: at some point the cell fails, so the FTL needs to be able to handle it, some drives have extra cells ( more than it shows to use it when they fails) 
**Wear leveling**  if a certain cell keeps, keeps the wear tf the drive on the same level, ftl copies data, multiple copies of the data, maybe when it gets deleted it is in different places of the drive 
Reorganize the data to uniformly wear out the cells. E.g. moving less used data to a more used cell.
**Data encryption and compression**

in a HDD head, sector, track, you literally tell the drive go here and read the content 

move around data, copy data and since there is the trimming part, it data as long that the drive is power on even if the OS is on
from the external point of view we don t have control, when we perform acquisation we dont get the physical data, we get the data that the FTL tells us, if tells 

only the ftl knows how to map the data, where to put the data, if compress, encrypt or obfuscate it

FTL obfuscate to protect the data from us, to don't allow us to change the FTL for another

Challenges in black box analysis and goals

Trim: the pre emptying of the blocks

a lot of use of chaching, if you need to do the same test more time you have to turn the caching off because it is going to impact 


TRIMMING 

you put data on the drive
quick format the drive 
stimulate the OS to tell the drive to trim everything 
you go back and read the data
if trim wa sactived it turnd on after 10s of inactiviti of the drive ( trim works when drive not active) 
forensic analis on SSD ( unless we are lucky) we do not expect to find file deleted


Gargbage collection
you feed the drive, switch to a forensic OS, quick format, and see what happens


____
In hdds we can reliably phisically address a sector from the OS and read it on the drive
In sdds FTL translates logical block addresses (LBA) as requested by the OS into the respective physical block addresses (PBA) on memory chips. 
The underlying mapping is completely transparent and can be modified by the FTL at any time for any reason. The FTL may move data around or blank data even if the OS is not running. 
**Most forensic approaches and tools rely on the ability of the OS to access the raw data on the disk.** 
Since the FTL decides how to compress and obfuscate data and shuffles it (for wear leveling, even when the OS isn’t running), it is the only one with the knowledge of the mapping between the logical structure of the data seen by the OS and the physical layout.
The FTL cannot be disabled via software. You can read the chips with external tools (extremely difficult), risking the destruction of the drive, extremely time and money consuming. 

----
We need a triage methodology 
We developed a simple and affordable black-nboc triage procedure to assess impacts of FTL on the use of a BB tools, assess likelihood of success of a white-box attempt. 
• SSDs implement techniques that are potentially disruptive to black box forensics
____

This means that the drive keeps changing also when connected to a write blocker. This is true also for the USB key, in this case often the FTL tends to “approximate” some data read, as a consequence the hash of the image of the USB drive is not consistent, it keeps changing.
