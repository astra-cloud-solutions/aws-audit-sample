## Cost Optimization Findings

### Executive Summary
- **Title:** Underutilized EC2 Instances Driving Unnecessary Spend
- **Risk Level:** Medium
- **Estimated Monthly Savings:** $480
- **AWS Pillar:** Cost Optimization
  
#### A. Overprovisionning
Identified a cluster of EC2 instances running background job processors. These instances were provisioned for a peak load that occurred only 2-3 times per month, but ran 24/7.

- **Resources:** 8x `c5.large` instances in `us-east-1`
- **Utilization:** Consistently below 15% CPU for 90% of the month
- **Cost:** $1,200/month ($150/instance)
- **Spike Handling:** Manual scaling via ops team tickets

##### Root Cause
The initial architecture used static capacity planning for a variable workload, considering background processors as critical always-on services.

##### Recommendation
1. **Immediate:** Right-size 6 instances to `c5.medium` (saving $480/month)
2. **Strategic:** Implement AWS Auto Scaling for the processor cluster
3. **Architectural:** Explore switching to Spot Instances for fault-tolerant workloads

##### Business Impact
- **30% reduction** in compute costs for this service
- Elimination of manual scaling overhead for operations team
- Better alignment of infrastructure cost with actual business usage
  
