----- Target Group -----

1. Target Type
	- instance type

2. Target Group Name
	- any name

3. Protocol	      = 	Port
        - Http/Https  = 	80/443

4. IP address type
	- IPv4

5. VPC
	- default/you can go with custom vpc

6. Health checks
	Health check protocol
		Http/Https

	Health check path
		/index.html

    Advanced health check settings
	Health check port
		Traffic port

	Healthy threshold   = 5
	Unhealthy threshold = 2
	Timeout		    = 5 seconds
	Interval	    = 30 seconds
	Success codes	    = 200

7. Tags - optional
	Key = Value


8. Register targets - recommended
9. Ports for the selected instances



------ Load Balancer -------

1. Load balancer name
2. Scheme = internet-facing
3. Load balancer IP address type = ipv4
4. Network mapping
	vpc = default
	Availability Zones and subnets
5. Security groups = default-sg
6. Listeners and routing 
	Protocol = http/https  Port=80/443
7. Default Action:
	Routing action
		1. forward to target groups
		2. Redirect to URL
		3. Return fixed response
8. Forward to target groups
	Target group = select a target group
9. Listener tags - optional
	key = value
