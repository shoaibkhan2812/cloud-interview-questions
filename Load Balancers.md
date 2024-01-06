### What's Load Balancer Warmup?

In normal scenarios the Load Balancer (or ELB in case of AWS) can handle large traffic when it increases gradually. However if a flash traffic is expected, like at launch of an awaited website, black-friday or holidays sale, the burst in traffic would be too high. So if the load balancers are left to scale up naturally, it may not be able to keep up with the incoming traffic. In such scenarios, its better to warm up the load balancers, so that they can handle the sudden spike in the number of requests.

AWS considers that if the traffic increases more than 50% in less than 5 minutes then it means that the traffic is sent to the load balancer at a rate that increases faster than the ELB can scale up to meet it. In such cases, one needs to contact AWS to do an operation called “pre-warming”. Ideally this request should be made atleast 36 hours in advance.

AWS will configure the ELB to an appropriate level of capacity based on few questions which they ask for configuring it like:
* Start and end dates of the expected traffic
* Expected request rate per second 
* Total size of a typical request

Unfortunately there's no automated way to do it and you need to contact your CSP(Cloud Service Provider) to warm it up for a specific event.

Sources:

https://petrutandrei.wordpress.com/2016/03/18/pre-warming-the-load-balancer-in-aws/

https://aws.amazon.com/articles/best-practices-in-evaluating-elastic-load-balancing/#pre-warming
