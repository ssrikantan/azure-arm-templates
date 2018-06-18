## SF ARM Templates - add to existing VNet, use existing Standard Load Balancers
Primary author of the ARM template - @anildwa

## Key settings and features implemented ##

1. Adds multiple  Node Types to the SF Cluster, the first Node type will have a 'Basic' SKU Internal Load Balancer. The rest of the Node types will have an existing Standard Load Balancer + Standard public IP Address each linked to them. The The URL of the existing Public IP Addresses (Standard SKU) need to be provided as an array. The number of Node types created would be based on the size of this array +1.
2. It adds the SF Cluster to an existing VNet and Subnet. 
3. An OMS Repository is created (SKU => OMS - per Node) and configured with the SF Cluster. The OMS Solutions for a) Container Monitoring and b) Service Fabric Analytics are added to the deployment and the SF Cluster linked to it. 
4. Managed disks are used for the VMSS in the SF Cluster and performance metrics are configured for capture
5. The Resource Monitor Service is configured in the SF Cluster, so that Service type instance auto scaling can be implemented.
6. Silver SKU for both the durability and reliability tier used. This is to ensure that scaling down of the Nodes in the cluster would properly remove the nodes from the SF Cluster as well, and that they do not show up as unhealthy in it.
7. The Port numbers for the Load Balancing rules and the Health probes are hard coded in the template.
8. Uses existing certificates in Azure Key Vault for inter node communication. It also requires the thumb print of the certificate on the local machine that would be the Admin client for the cluster.
