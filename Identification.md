# Identification
## 11/03/22
 ### Recovery of deleted data

Most typical task-> recover of deleted tasks
in many cases the information may have been deleted volontarly or not. Sometimes deleted very unvolontarly. 
Rarely machines get presaved. Usually the machine have been used after, so things are modified. File system, many cases the investigation takes places years after, so damaged can occur. In a typical case in crime, the first analysis of evidence takes place months after evidence has been collected, court case years after. 


How do we retrive data that has been deleted? 

How data are organized: 
unix file system is basically the same as creative an archive. We have a lot of data, spread and then a set of index cards that tells us where to find the data in the archive. If we lose the index the data is still going to be there, we just don't know where it is. On hard drives we have a et of metadata that describes the data, is written in the fyle sustem by the OS ( has the tasks of organizing drives). in the FS there are pointers to the data organized acc to a file structure. We have I noeds that rae blocks of information containing direct pointers to data blocks, double.. and so on. 
You can link file with permission to its content directly, undirectlu, double undirectlu..
When we deleta file the OS writes 'has been deleted'. But the metadata is still there. At some point the operating system will take away the label (inode) but the content will still be there, just do not know where. At some point ( before or after the previous) the OS is going to overwrite the blocks ( even if they are still linked(linked since marked as deleted. This two things happen randomly. 
1. file marked but as deleted but still present
3. blocks but mis metadata
4. metadata but not file
not deleted earlier than it needs to, happens randomly, but since drives are large, it is rare that the OS need badly to overwrite blocks. it is more lakely that the metadata go away-> when the OS rewrites the file system ( because does file system check ecc) 

metadata before blocks rewritten but it is random 

until the metadata desapper we can recover information ( where, position, when ) 
until the blocks are overwritten we can recover the data on the disks we just don't know where they are


follows the metadata and rewrites before deleting the metadata: only way to be sure they are deleted



In older drives.. the situation is different set of tracks organized in cylinder
minimun arch/unit that is designed to read: a sector
sectors, basic amount of space that you can address but drives have different secots, OS do not alloate file based on sectors but on clustes( bunch of sectors) 

no sub units, use it or not use it. OS considers them one of a time.
file: not a multiple of a cluster, takes an entire cluster + a bit. but occupies also the second. 



since data only goes away when overwritte, the last space allocated but not sostituito, will still keep the data from the previous file. this space is allocated(cannot be overwritte) and contains the data of the previous file that could be one deleted many years ago. If the file allocated on top is a file that stays there. 

zip file: can i find them in a ** space??random noise. 
I can find chunk of a video but very small
what i could find: CHUNK OF TEXT, xml pages, blocks of texts belonging to files, to old windows document folders 

how de we recover data deleted? 
if ther eis still the metadata: easy 
we look at the metadata, if not overwritten recover it. we know where it is 
if we don't have the metadata, more complicated. the data may be on the drive but do not know where
techique: CARVING: you scan the entire drive sector by sector as a stream of bits, you scan it for the headers of known file types, at some point we find, from there we search for the footer. we assume that whatever is in the middle is the file. if it is the entire drive, header and footer are not ht esame file. they try to estimate a ragionevole size. 
fragamatation, used to be one of the problems, the point is, if you are saving a file on a very large drive you can save it all together, on a small drive forced to break it and fragment it. when you read it sequentially is faster than if it is fragmented. 

on modern drives in reality fragmentation is an unknown problem..at most in two, one has the header and th eother has the footer
**Header and footer**-> typical partitions. 

Tools: 
most forensics tools allows you to create a timeline

gpart, testdisk: craving 
photorec: best tools for recovering images on windows machines, some of the most criminal cases relate to pictures. 

MAC values, modifies accessed changed-- these data , OS record the last entry of this data, last time accessed / modified. if you pick up all the fils an you think to plot the last time, you create a time line that in the recet times is very complete, as you go backwards, since inly the last time is recorded, the more you go back the more you have holes. very good rep of the activity of the system 


 ### Antiforensic techniques
-Transient and definitive
transient:all the tech that can hgide evidence and confuse analysti provides he doesn't knows
definitive: destoys the evidence

most against the tools that the analyst uses. against acquisition and analysis
acquisition: impossible to acquire-> usually definite
identification: they tend to fold under transient, confuse the tools, not find evidente

- Timeline tampering (definitive)
antiforensic can targed data used to create a timeline, MACE dara 


- Countering file recovery (definitive)
some utility move around files moving only the valid data and zeroing the ***


-Fileless attacks-> definitive
attacker, after exploitation, not while on disk, happens only in memory 

- Filesystem Insertion and Subversion Technologies (transient)
space reserved, fill with data that no one is going to loof for, transient, data is there and if we were suspect that someone uses tis techique we could find it


can read ext3 partition with ext2 ( ignores a hournal) 
if you build a fake ext3 journal and place data there, ext2 ignores it. tools ignores it assuming is a strange journal
inodes marked as directories KY FS ???
Data muse Fs puts the data in padding, empty aresa tipically ignored bu forensics tools-> cute idea, no one really uses it 

-Log analysis- transient
rare forencis analyst looks at logs one by one, many times pre made scripts. if you are an attacker that is doing that, you may rewrite logs in a way that breaks those scripts
inject columns, something that breaks the structure of the logs, breaks down on a line and skips stuff to be nascoste 

-Partition table tricks
fill uo partition that is overlapping
in reality peolple have few partitions, bizzarre behaviours, one tool names partitions in the same ways windows does ( A,b,c,), in windows if you go beyond 20 partitions, the next is AA.. starts using two letters ncase ( the tool) doesn not do that, the 22 don't show up. inconsistency show uop if you have a large number of partitions. 



