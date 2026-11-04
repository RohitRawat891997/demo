# AWS Application Load Balancer (ALB): Hands-On Practice

This guide walks you through creating an internet-facing Application Load Balancer and connecting it to EC2 instances with a target group. An ALB receives web requests and forwards them to healthy targets, such as EC2 instances.

> **Before you begin:** Have a VPC with at least two public subnets in different Availability Zones, and EC2 instances running a web server. The instances should return a successful response at `/index.html` (or update the health-check path below to match your app).

## How the pieces fit together

**Browser → Load balancer listener → Target group → EC2 instance**

- A **listener** accepts requests on a protocol and port, such as HTTP on port 80.
- A **target group** contains the EC2 instances and checks whether they are healthy.
- The **load balancer** routes requests from its listener to the target group.

## Practice: Create a target group

1. Open **EC2 → Target Groups → Create target group**.
2. Choose **Instances** as the target type.
3. Enter a target group name, for example `web-servers`.
4. Choose **HTTP** as the protocol and **80** as the port, assuming the web server on each instance listens on port 80.
   - The target group's protocol and port describe traffic sent **from the load balancer to the instances**.
   - For a common HTTPS setup, the browser-to-load-balancer connection uses HTTPS, while the load-balancer-to-instance connection can use HTTP.
5. Choose **IPv4** for the IP address type and select the VPC that contains your instances.
6. Configure the health check:
   - Protocol: **HTTP**
   - Path: `/index.html`
   - Port: **Traffic port**
   - Healthy threshold: **5**
   - Unhealthy threshold: **2**
   - Timeout: **5 seconds**
   - Interval: **30 seconds**
   - Success codes: **200**
7. Optionally add tags, such as `Key: Environment`, `Value: Practice`.
8. Select **Next**, choose the EC2 instances to register, confirm port **80**, then create the target group.

Wait for the target group's registered instances to show **Healthy**. If they do not, check that the web server is running, the health-check path returns HTTP 200, and the instance security group allows traffic from the load balancer security group on the target port.

## Practice: Create the load balancer

1. Open **EC2 → Load Balancers → Create load balancer** and choose **Application Load Balancer**.
2. Enter a name, for example `practice-web-alb`.
3. Set **Scheme** to **Internet-facing** and **IP address type** to **IPv4**.
4. Under **Network mapping**, select the VPC used by the target group and choose public subnets in at least two Availability Zones.
5. Choose a security group for the load balancer. It must allow inbound web traffic from your intended clients:
   - For HTTP practice: inbound TCP **80** from your allowed source (for a temporary public demo, this may be `0.0.0.0/0`).
   - For HTTPS: inbound TCP **443** from your allowed source.
6. Under **Listeners and routing**, configure an HTTP listener on port **80** and set its default action to **Forward to target groups**. Select `web-servers` (or the name you chose).
7. Optionally add listener tags, then create the load balancer.

> **Security note:** Avoid relying on a broad default security group. Use dedicated security groups. The EC2 instance security group should allow the application port (for example, TCP 80) **from the load balancer's security group**, rather than opening that port to everyone.

## Test your load balancer

1. Wait until the load balancer state is **Active** and the target group targets are **Healthy**.
2. In **EC2 → Load Balancers**, select your ALB and copy its **DNS name**.
3. Open `http://<load-balancer-DNS-name>` in a browser. You should see your web page.
4. If the page does not load, check the listener, target health, subnet routing, and both security groups.

## Optional: Add HTTPS

To serve HTTPS, request or import an SSL/TLS certificate in **AWS Certificate Manager** for a domain you control. Add an HTTPS listener on port **443**, attach the certificate, and forward requests to the target group. You can optionally configure the HTTP listener to redirect visitors to HTTPS.

## Quick reference

| Setting | Practice value |
| --- | --- |
| Target type | Instances |
| Target group protocol/port | HTTP / 80, if instances serve HTTP on port 80 |
| Health-check path | `/index.html` |
| Load balancer type | Application Load Balancer |
| Scheme | Internet-facing |
| Address type | IPv4 |
| Listener | HTTP / 80 (or HTTPS / 443 with a certificate) |
| Listener action | Forward to the target group |

When finished practicing, delete the load balancer and target group, and terminate any test instances you no longer need to avoid ongoing charges.