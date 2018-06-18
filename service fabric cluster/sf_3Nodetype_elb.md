## SF ARM Templates - add to existing VNet, and adding Basic SKU external Load Balancers
Primary author of the ARM template - @anildwa

## Key settings and features implemented ##

1. Adds 3  Node Types to the SF Cluster, that can be accessed using an external Load Balancer
2. It adds the SF Cluster to an existing VNet and Subnet. 
3. Managed disks are used for the VMSS in the SF Cluster and performance metrics are configured for capture
4. The Port numbers for the Load Balancing rules and the Health probes are hard coded in the template.
5. Uses existing certificates in Azure Key Vault for inter node communication. It also requires the thumb print of the certificate on the local machine that would be the Admin client for the cluster.
