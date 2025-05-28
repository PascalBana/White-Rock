first and foremost there are 7 layer to the OSI (Open Systems Interconnection Reference) Model, to list them quickly they are
	- Layer 7 - Application
	- Layer 6 - Presentation
	- Layer 5 - Session
	- Layer 4 - Transport
	- Layer 3 Network
	- Layer 2 Data Link
	- Layer 1 Physical
Now to go into more detail over each of these layers. This is a model don't over think it. You will often reference this Model as it is very useful to communicate where an application sits between other technical folks. it is just Abstract enough to where everyone can understand what your talking about. so it is very good for communication purposes.

Layer 1 - Physical Layer
	This is literally the cables that connect everything, literally the physical connections. if someone says you have a layer 1 problem it usually means your cables are fucked. that or something close to your cables like [[adapter cards]].

Layer 2 - Data Link Layer 
	The basic network "language". this layer uses DLC(Data Link Control) protocols. A good example is MAC(Media Access Control) addresses on Ethernet. any problem with device connection such as when connecting to a MAC address is usually referred to as a Layer 2 problem.

Layer 3 - Network Layer
	Also known as the "routing" layer, this is where IP comes into play. this includes something called IP fragmentation. this is when a packet is to large to be sent whole so the packet is fragmented into multiple smaller IP packages and sent over the network. if you have a fragmentation problem or packets aren't arriving this is often referred to as a layer 3 problem.

Layer 4 - Transport Layer
	This is where TCP and UDP come into play, if you have a TCP or UDP problem then its considered a Layer 4 problem

Layer 5 - Session Layer
	 It should be stated layers 5, 6, and 7 are all dealing with similar stuff so lines can get blurry. This is where Communication management between devices occurs(Start, Stop, Restart). Control Protocols happen here. And the all important... This layer is where Tunneling takes place, so if you ever open a tunnel its on Layer 5.

Layer 6 - Presentation Layer
	The layer just before your able to actually see the application is Layer 6. This is where Character Encoding occurs. Also this is where encryption and decryption occurs(SSL/TLS). Many layer 6 Applications are also layer 7 Applications, again lines get pretty blurry up here.

Layer 7 - Application Layer
	 This is the Layer we can physically see


It is very important to remember that layers 1 through 4 have very distinct lines drawn between them but layer 5 through 7 are all bundled together. if your having a layer 2 problem, then you can be pretty certain whats going on. but a layer 6 problem could actually be getting effected by layers 5 or 7. they are much more interconnected and therefor need to be treated as one sudo layer when doing a lot of problem solving