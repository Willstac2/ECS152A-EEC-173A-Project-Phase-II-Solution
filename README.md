Download link :https://programmingsolver.com/questions-and-answers/ecs152a-eec-173a-project-phase-ii-solution/

(It is your responsibility to schedule an appointment with the TA for the demo, at which time you need to turn in your Phase II report also. All partners must be present for the demo and be able to respond to the TA’s questions.)

1. Introduction

In this phase, we will extend the single-server and single-queue simulation model developed in Phase I to model multiple independent hosts that communicate using the token passing protocol, e.g., a token ring. The goal is to analyze the behavior of the token passing protocol, namely the throughput of the channel and average packet delay. The following references and resources will be used in this project.

Lecture/discussion materials.

Textbook: J. F. Kurose and K. W. Ross, “Computer Networking, A Top Down Approach,” Chapter 6.

Schedule, milestones, and other administrative issues related to this project are the following:

You are required to submit a final write-up for Phase II of the project. The write-up should contain:

A brief description of Phase II implementation logic

Hard copy of the code for Phase II

Phase II results

Analysis of Phase II results

In Phase II, you will be asked to explain your code and demonstrate your results to the TA during office hours or additional time slots set aside for the demonstrations. The schedule for project demonstration will be announced later.

There may be questions related to this project in the final exam.

1

2. Simulation Analysis of a Token Ring based LAN

In this project, you will build a discrete-event simulation model to study the behavior of a token ring protocol for Local-Area Network (LAN). The first Phase of the project included the implementation of a single-server queue model. Now, in Phase II, we focus on modeling and analysis of token ring based LAN. This modeling will require the single-server model implementation of Phase I. The system model is shown in Fig. 1.

…….

Host 1

Packet

Packet

Host 10

Packet

Host 2

Packet

Host 9

Host 3

Packet

Packet

Host 8

Host 4

Packet

Packet

Host 7

Host 5

Packet

Host 6

Packet

Figure 1: Model of token passing protocol, e.g., token ring.

In order to develop the simulation model, we will make the following assumptions:

Let N denote the number of hosts. As before, λ will denote the mean arrival rate of packets at each host. All hosts are identical, and each host sources packets with a mean arrival rate of λ packets/second. The arrival process follows a negative exponential distribution (same as in Phase I of the project).

Each host has an infinite FIFO buffer to hold outstanding packets.

2

Length of each packet is an independent random variable which is uniformly distributed in the interval [64, 1518] bytes. Each packet will choose a destination randomly from all the other hosts with equal probability.

Each host monitors the ring until it detects and captures the token, also called a “free” token (hereafter referred to only as token). A host may only transmit when it receives a token.

When a host receives a token, it holds onto the token only if it has some packets to transmit; otherwise, it immediately forwards the token to the next node.

If a host has some packets to transmit when it receives the token, it transmits all the packets in its queue (and this set of packet transmissions is called a frame) to the next host. While the frame is circling the ring, no token is on the network, which means that other hosts wanting to transmit must wait. Therefore, collisions cannot occur in token ring networks. (Other variations of transmission strategy are also possible.)

The frame is forwarded by each host on the network until it circulates back to the source host, where it is removed. Then, the source host immediately releases the token back to the ring, giving other hosts the opportunity to transmit frames. (The destination, like other hosts on the ring, will also forward the frame to the next host; but it will also make a local copy for itself.)

Enhance the code that you have developed in Phase I to model the above system. In this phase, we are interested in two parameters for investigating the token ring-based LAN’s performance. We want to measure them by the influence of different number of hosts and the arrival rate:

Throughput: Throughput is defined as the number of bytes transmitted per unit time. In the simulation, you can count the number of bytes that are successfully transmitted and divide that by the entire simulation time to find the throughput.

Average packet delay: We intend to find average packet delay for the overall network. In the simulation, this delay includes the queuing delay and transmission delay for each host, and the propagation delay between the hosts. For our purposes here, assume propagation delay to be 10 microseconds for each link and channel transmission rate to be 100 Mbps.

You need to obtain the following results:

Plot the throughput and average packet delay as a function of λ . Let number of hosts, N=10. Obtain the throughput for the following values of λ = 0.01, 0.05, 0.1, 0.2, 0.3, 0.5, 0.6, 0.7, 0.8, and 0.9 packets/sec.

Repeat part [a] with N = 25.

Note that, to present your result clearly, it is better for you to plot two figures: one for throughput, and the other for average packet delay.

You have to submit: (1) a brief description of your Phase II implementation logic, (2) your source code, (3) plots of your results, and (4) a write-up on an analysis of your results.

Interactive grading will also be required. Please sign up for a time slot with the TA.

加QQ codinghelp Email: programminghelp1@proton.me
