# Linear to Physical Address Translation
- Segment address translation converts the logical address to 32 bit linear address.
- Linear address contains three fields:
  - Dir field: 10 bits (Used to lookup in the directory table)
  - Page field: 10 bits (Used to lookup into page table)
  - Offset field: 12 bits (Used to select a location from page frame)
- Page directory entry is present in the page directory base register (PDBR) (CR3). It contains the base of the page directory
  and offset is taken from the directory field.
- Then the base address and directory bits taken from the linear address together gives up the page directory entry which act as the 
  base for the page table.
- The base from the page directory and the offset of the page table from the linear address gives us the page table entry.
- The page table entry gives us the base address for the page which together with the lower 12 bits that is the offset help us to 
  compute the actual physical address.
- Illustration of this whole layout as a book. 
Book is like a page directory table which consist of indexes for various chapters. Here chapters are the various pages. And then
there are many subsections in a chapter which is used to get to the actual line in the book which is the actual physical address.

## Page directory entry
- To enable paging CR3 and CR0 registers must be enabled.
- It is 32 bits.
- 0-12 lower bit address contains these information:
  - 0: P(Present) -> If this bit is set that means the page is actually present in the physical memory at this moment. If page is 
                     not available due to swap then page fault will occur. 
  - 1: R/W(Read or Write) -> If this bit is set, the page is read/write. If not set then this page is read only. 
  - 2: U/S(User or Supervisor) -> If this bit is set, then it can be accessed by all. If not set then this page can be only accessed by supervisor.
  - 3: W(Write Through) -> If set then Write though caching is enabled, if not then write back is enabled.
  - 4: D(Cache Disabled) -> If set then page will not be cached
  - 5: A(Accessed) -> Bit is set when the page is accessed i.e. read or written to
  - 9-11: AVI(Available) -> Bits are available to user
  - 12-31: Page table address -> Physical address of the Page table
  
## Page table entry 
- PDE contains physical address of PTE.
- 32 bit
- Same as PDE but contains extra 
  - 6:D(Dirty Bit) -> If set page is changed.
  - 12-31: Page frame address
