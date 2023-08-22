why build distributed systems?

- some applications are inherently distributed (like the web)
- Others require high availability and need to be resistant to single node failures (Dropbox)
- Some require handling workloads that are too big for a single node (Google Search)
- Others have requirements that would be physically impossible to achieve with a single node (Netflix)

# 1.1 Communication
How are the requests and response messages represented on the wire?

