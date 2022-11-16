# File System that keeps its contents in primary memory, TecnicoFS

The final objective of the project is to develop a file system (File System, FS) in user mode
(user-level) and which keeps its contents in primary memory, called TecnicoFS.

The FS in user mode are an alternative that has been gaining relevance recently, as
that allow the rapid development of easily portable FS with strong fault isolation,
as will be discussed in theoretical classes during the semester. In a user-mode FS, the
FS functionalities are offered in a server process (which, of course, runs in
user). Other processes can call FS functions through requests to the System kernel
Operative, which, in turn, forwards these requests to the FS server process through a channel
of communication established with this. Afterwards, the return of the function is sent back to the client.
invoked in reverse.

Unlike traditional FS, which store information in blocks (e.g., on a magnetic disk or
SSD), TecnicoFS is designed to store the contents of your files and directories in memory
primary. It can, for example, be used to keep a temporary, non-persistent FS in memory.
DRAM, thus benefiting from the better performance of this memory, compared to disk/SSD.
It can also take advantage of new persistent memory technologies when used on machines
where they are available (such as the latest Intel-enabled DIMMs)
Optane DC).

## Authors

Group 23

92513 Mafalda Ferreira

92553 Rodrigo Antunes

## First Delivery

Develop the TecnicoFS server, composed of a pool of slave tasks that
perform FS operations on the shared directory in memory. At this stage, there are some
important simplifications: i) only create, search and remove operations are supported
directory/file; ii) the synchronization of concurrent accesses uses a simplified strategy
with just one global latch; iii) calls to TecnicoFS functions by client processes
are not yet supported; instead, calls are simulated by loading a file
containing sequences of commands.

## Second Delivery

Extend the previous solution with a finer sync, which will allow for greater
effective parallelism. It also improves input file loading to allow
operations run in parallel with the initial file upload. Finally, extend the API
of FS with the file rename operation, with atomic semantics.

## Third Delivery

Extend the previous solution by supporting process invocation of FS operations
client. Client processes make calls to TecnicoFS by sending messages through a
socket, which are consumed by tasks on the server and which respond to clients with their
result. Additionally, it implements the operations missing from the TecnicoFS API.
