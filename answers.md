
1. The minimum seek time for an HDD is 9msec, and the maximum seek time is 90msec. The block size of this HDD is 4KB. How long on average does it take to read 100MB of data?

Well the simple answer would be to assume that the average seek time will be the average of the maximum and minimum seek time.  Therefore you would be left with an average seek time of essentially 50 ms.  That means you could access around 20 blocks per second.  Given that there are 4KB in a block that means you can access .08mb of data in 1 sec.  To reach 100mb of data would then take 1250 seconds or 20.8333 minutes.  This is assuming that each new block will have the same seek time as the first block.  This is generally not the case and although the most simple probably also the most inaccurate.  So lets assume that we can do a continous read of the data.  In this case we only need to factor for the seek time once.  Now what becomes significant is how fast the disk spins and how many blocks are on a track.  lets assume a rotational speed of 7200 rpm and 63 blocks per track.  So we know we need to read 25000 blocks of data given we have 100 mb of data in total and each block is 4 kb.  No we must divided the amount of blocks by the blocks per track to know how many times the disk must rotate.  The answer is roughly 400 times.  Given a disk that rotates at 7200 RPM that means the disk spins about 120 times per second.  Since we must spin 400 times in total to reach all the data after the intitial seek it would take 3.33 seconds. We must also add on the intial seek time which we can guess to be 50 ms.  This brings are total time to 3.38s.  Of course this answer does not account for many factors such as the time it may take to switch tracks along with other possible latency issues.  However, given the information provided this is the best conclusion I can come to.

2. Describe a TCP/IP packet in detail. Describe the header, how many bytes it is, and which components it contains. What data can come after the header?

An IP packet consists of a header and a data section.  The header contain s information thats realted to it reaching its destination.  It consists of 32 bytes.
It contains these components(assuming IPv4):
Version - 4 bits, for IPv4 it is 4
Internet Header Length - 4 bits, specifies the size of the header
Differentiated Services Code Point - 6 bits, for tech that needs realtime data streaming
Explicit Congestion Notification - 2 bits, a way to notify endpoints of network traffic
Total Length - 16 bits, gives details on the whole packets size
Identification  - 16 bits, way to uniquely identify fragments
Flags - 3 bits, each bit is used to flags in relation to fragments, first is a reserved bit, the second is DF or don't fragment, the third is MF or more fragments
Fragment Offset - 13 bits, specifies the offset of a fragment
Time To Live - 8 bits, limits lifetime to prevent persistence of data stuck in purgatory
Protocol - 8 bits, defines the protocal used
Header Checksum - 16 bits, used to check for errors by comparison with the expected sum
Source Address - 32 bits, IP address of the packets sender
Destination Address - 32 bits, IP address of the packet receiver
Options - 16 - 128 bits, although not often used

The data portion may contain many different things such as the status, errors, messages, etc... The way that it is read is determined  by the protocol in the header.

3. How does the network protocol guarantee that a TCP/IP packet is complete after transmission?

Packet delivery acknowledgement is handled by TCP since IP does not guarantee delivery although it does try its best.  The TCP uses a two-way handshake process when ending an end to end connection.  First a FIN(finish bit set) is sent as a connection termination request to the other device.  The recipient responds with an acknowledgement indication the FIN was received.  The process is not complete until both side have sent a FIN and received an acknowledgement.

4. What is the difference between TCP and IP?

Simply, the TCP handles delivery of the packet while the IP is responsible for the addressing.  The TCP will guarantee delivery of the data to the address the IP is responsilbe for.
5. Why is 3d performance so much higher with a graphics card than without? Modern CPUs are extremely fast, what is limiting their performance?


Well.. CPU's are designed to do a large amount of different tasks.. A jack of all trades.  While GPUS are designed to be good at repetitive work and not so much at switching tasks.  3d requires transforming and projecting a 3d triangle onto a 2d screen. This is takes alot of intensive repetitive work to do in realtime.  By having a dedicated GPU it can handle most of this repetitive work while the CPU can handle higher level things. GPUs are also increasing in power and flexibility so they are getting bettter at handling more and more of the 3d process.  CPUs are still very important to this process the GPU just takes some of the burden off of the CPU.  This is why they work so well together.  In terms of structural difference GPUs have a large amount of ALUs but these ALUs are grouped together so the members can only work on the same or close to the same task.  Contrast this to CPUs who are designed with the ability to immediately switch tasks and account for all kinds of things.  Another huge difference is the amount of instructions per clock that can be executed is vastly more superior in a GPU.  GPUs are made up of hundred of small cores but these are slower, simpler, and lower operating frequency cores.. very different from a modern CPU.  My theory on why CPUs are not made up of many many cores like GPUs is because the cores must be able to handle a wider range of problems.  Each core must be more flexible and powerful. Therefore the size of the cores in the CPU are much larger (probably more expensive) and im sure people dont really want much larger much more expensive laptops and computers when theyre already really fast and really good at doing 99% of tasks.
