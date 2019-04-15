# Segmentation 
- Process of converting logical address to linear address.
- Logical address is of 32 bits where lower 16 bits represent offset and higher 16 bits represents selector.
- To convert it to linear address, the selector that is higher 16 bits are multiplied by 8 and looked up in the selector table.
- In the selector table, we have segment descriptor which consist of access right, limit and base address.
- Base address is added to the offset that is the lower 16 bits of the logical address to form the linear address.
- If paging is not enabled then this linear address is the physical address and we could access the physical memory.

