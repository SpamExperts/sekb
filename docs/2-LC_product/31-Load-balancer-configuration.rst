.. _2-Load-balancer-configuration:

Load balancer configuration
===========================

If you prefer to use a physical load balancer to distribute your traffic
over the SpamExperts Local Cloud nodes ( outbound or inbound traffic),
you should ensure the load balancer transparently forwards the real IP
address at network level.

The most common setup consists of:

1. Hardware load-balancer communicating with the SpamExperts nodes via
   an internal-IP address
2. The SpamExperts nodes use the load balancer as gateway for the
   internal traffic which handles the communication back to the source
