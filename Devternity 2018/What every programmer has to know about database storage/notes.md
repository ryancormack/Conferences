# What Every Programmer has to Know About Database Storage
> Alex Petrov

Access patterns
- Sequential and random

## Sequential
Sequential access requires in memory buffering and sorting. It can then be written in an append only manor

This has several hardware costs 
- HDD arm seek
- SSD erase/program cycle
- Garbage collection

## Disk data structures
 ### Mutable
 - Fragmention of written blocks
 - In place updates can happen

 ### Immutable
- Sequential writes

## Log Structured Storage
Data is stored in memory, with many reads and writes happening here. This is eventually then written to disk where reads happen

- Sequtenital writes
- No memory overhead
- Involoved read path
- Maintenance costs

This storage is write optemised, but reads then become expensive as they have to read memory and disk and merge the potential two stores together

## B Tree
Requires a write overhead to find the correct place to write the data. This allows faster reads as there is no memory/disk lookups and merging

Each write node has overhead to allow resizing without having to shift the whole store every time a single node needs to be resized. Each update then requires the whole node to be overwritten

Range scans can help with reading

Growing any node is expensive. And writes have to be propogated up, which may then make the parent need to split up, and so on

This makes in place updates expensive.

## Summary
DB's have a trade off of read optimised, write optimised and space optimised