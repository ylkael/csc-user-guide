---
search:
  boost: 2
---

# What is Pouta?

The Pouta service is composed of two different and independent IaaS services, [cPouta](https://pouta.csc.fi) and [ePouta](https://epouta.csc.fi). The cPouta cloud is the general purpose public cloud platform. The ePouta cloud is the sensitive data cloud platform. If you handle sensitive data you must use ePouta. Both the cPouta and ePouta clouds run on the [OpenStack](https://www.openstack.org/) cloud software. The Pouta cloud services offer on-demand virtual infrastructure and are suitable for most kinds of computational workloads and any other supporting services these workloads might need.

## cPouta

The cPouta virtual machines can be configured to be accessible from the Internet. This allows customers to run widely available services. The virtual machines do not have access to any other part of CSC's infrastructure, other than what
is already visible on the Internet. Application data and software must
be uploaded either via the Internet or copied from CSC's existing
shared storage services.
 
## ePouta

The ePouta cloud service is designed to handle sensitive data. It follows the technical and legal requirements necessary to store data securely. The ePouta cloud virtual infrastructure is only accessible via the customer's own network
infrastructure. It is independent and isolated from the rest of CSC resources, including other customer's ePouta infrastructures. It can be used to analyze sensitive data which may require large amounts of memory or clustered I/O performance, a remote
desktop for processing sensitive data etc.