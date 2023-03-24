# RPL attacks using WSN motes
Contiki Os and Cooja simulation project  
RPL is a routing protocol for low-power and lossy constrained node networks.It creates a tree-like routing topology called the destination-oriented directed acyclic graph (DODAG), which is in the direction towards one or more nodes known as  root node or sink node. RPL protocols are used with resource constraint nodes. 

• **DODAG Information Object (DIO)**:it stores information including   rank of a node, RPL Instance, the IPv6 address of the root or sink and so on.
 • **Destination Advertisement Object (DAO)**: it consists of information that can used for downward traffic towards child nodes.
 •** DODAG Information Solicitation (DIS)**: Used by nodes to request graph related information from the neighboring nodes.
 • **Destination Advertisement Object Acknowledgement (DAOACK)**: Sent by a DAO recipient in response to a DAO message. 

Whenever a new node enters into a rpl network, it starts sending a DIS message to all nodes and waits for DIO message to be received whcih contains details regarding node id and objective code point. The DIO messages are broadcasted  at particular intervals based on the trickle algorithm. The node on recieving the info , calculates the rank . and based on that it selects a parent . To  send a message downwards , node should send a DAO message  containing the routable fixes up the tree.To prevent the loops ,RPL  does not allow the data  going in down direction and sent from a desecendent . RPL uses two header options which
Is flow of direction (O)and rank error(R) . Rank error is a flag set when there is a mismatch in the rank of sender and direction of flow.

When a malicious node is introduced into the network ,it can manipulate the header-options used by  RPL to track DODAG. Once the header-options are manipulated , the malicious node can cause denial of service attacks ,drain power from nodes and also can target certain nodes by creating black hole.


**DODAG attack using fit iot lab**
Here we have implemented a flood attack on a real testbed using the m3 node ( at86rf231) at site=grenoble. We flashed 1 up-UDP-server and 3 RPL-UDP-clients.  Here we have considered a flooding attack. The power consumption is shown in the figure. We modify the DIS-related code to define multiple DIS constants which causes the node to send DIS messages repeatedly. We also modify the timers to send the multiple DIS messages. We start a serial -aggregator and power consumption monitor which is used to capture the packets and also measure the power consumed at each node.
