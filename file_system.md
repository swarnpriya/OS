# Important Points:
- We need on-disk data structures to represent the tree of directories and file. This data structure should record 
  - Indentity of the block in memory holding the file content
  - Also should help us to track through the disk memory to see which part is free.
  - There should be in-memory cache. 
## Inode:
- It reperesents individual files. 
- It is a data structure containing these fields
  - A unique i-number
  - Block holding the file content
## Directory:
- It represents directory that holds the file 
  - File name 
  - i-number
## Path:
- Holds the path to the file
## File descriptor

### We should decide where we want to store inodes and content blocks on the disk. 
## Disk:
- Disk is divided into several blocks. 
  - Block 0 is bootstrap we should not use it. 
  - Block 1 is superblock (contains metadata about the file system like
                           file system size in block, 
                           number of data blocks, 
                           number of inodes,
                           number of blocks in log etc)
    It builds initial file system.
  - Block starting at 2 holds the log 
  - After the log we have inodes per block.
  - Bitmap blocks which keeps track of which data block is in use and which is free
  - Data blocks are either free or holds the content of the file or directory.
  
 ### On-disk inode:
 - Every inode is of same size. So if we are referring to nth inode it means we need to find nth inode on the disk. 
 - Fields 
   - type: Distinguishes between files, directories and special files. 
 ```
 struct dinode {
      short type;       file type (file or directory)
      
