### 1. Compare Static routing and Dynamic routing with regards to scaling, security and resource usage (Your answer should contain more than 20 words)

In static routing, remote networks are manually entered into the route tables whereas in dynamic routing the remote routes are automatically learned using a dynamic routing protocol. Due to this, the following differences can be observed.

- Scaling: Static routing is suitable for simple topologies as the routes must be configured manually. While dynamic routing is suitable for both simple and complex topologies.
- Security: In static routing, the routes are not advertised over the network by the routers like in dynamic routing. therefore it is more secure.
- Resource usage:  Dynamic routing requires processing power to calculate routes and consumes bandwidth to communicate routes over the network. Therefore resource usage is higher than static routing.

### 2. Briefly explain the 3 primary uses of Static routing (Your answer should contain more than 20 words)

- Providing ease of routing table maintenance in smaller networks or simple topologies.
- Routing to and from stub networks which are accessed by a single route, and the router has no other neighbours. Because there is no need of using dynamic routing protocols to calculate the route as there is only one possible path to that network.
- Using a single default route to represent a path to any network that does not have a more specific match with another route in the routing table.

### 3. List and briefly describe the types of Static routes

- **Standard Static Route:** Use for connecting to a stub network where there are no other routes.
-  **Default Static Route:**This is simply a static route with 0.0.0.0/0 as the destination IPv4 address and it matches all packets. It identities the gateway IP address to which the router sends all IP packets that it does not have a learned or static route.
-  **Summary Static Route:**This is used to represent several networks (with a contiguous set of addresses) that are on the routing table using only one IP address. This helps to minimize the number of static routes in the routing table
-  **Floating Static Route:** Also known as Backup route.  If the primary link used for communication between two stations fails this floating static route can be used as a backup route.

### 4. List the steps involved in creating a static route. List the cisco cli commands needed to create a static route, in the correct order from the start of the router. Also mention different options you can use when creating static routes.
(Your answer should contain more than 20 words)

Go to  the global configuration mode of the router

Router> enable
Router# configure terminal
Router(config)#ip route [network-address] [subnet-mask] [ip-address | exit-intf] [distance]
