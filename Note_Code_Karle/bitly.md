### Summary  
This video by codeKarle walks through designing a URL shortening service (like TinyURL), covering functional/non-functional requirements, short URL length calculation, collision-free ID generation, core architecture, and analytics integration. It addresses scalability, low latency, and high availability, proposing iterative solutions to avoid single points of failure and optimize performance.


### Abstract  
The video begins by defining functional requirements (shorten long URLs, redirect short URLs to long ones) and non-functional requirements (high availability, low latency). It calculates short URL length using a 62-character set (A-Z, a-z, 0-9), noting 7 characters support 3.5 trillion unique URLs—sufficient for large-scale use.  

Initial architecture uses a Short URL Service with database storage, but collision risks arise from concurrent ID generation. A Redis-based counter is rejected due to single-point-of-failure and scalability issues. Instead, a Token Service (on MySQL) assigns unique token ranges to service instances, which generate IDs in-memory (converting base-10 tokens to base-62 short URLs) and request new ranges when depleted. Unused tokens from crashed instances are acceptable losses given the vast ID pool.  

For analytics, the video suggests capturing request metadata (platform, user agent, IP) but warns against synchronous Kafka writes (latency impact). It proposes asynchronous Kafka calls or local aggregation (batched writes) to balance latency and data loss, then uses Hadoop/Spark for analysis. Cassandra is chosen for URL storage over MySQL for scalability, though sharded MySQL is an alternative.


### Main Points  
- **Requirements**: Functional (URL shortening/redirection); Non-functional (high availability, low latency).  
- **Short URL Length**: 62-character set (A-Z, a-z, 0-9); 7 characters = 3.5 trillion unique URLs.  
- **Collision-Free ID Generation**: Token Service assigns unique ranges to service instances; instances generate IDs in-memory, request new ranges when depleted.  
- **Architecture**: UI → Load Balancer → Short URL Service instances → Cassandra (URL storage); Token Service (MySQL-backed) manages ranges.  
- **Analytics**: Capture metadata (platform, user agent, IP); use asynchronous Kafka writes or local aggregation (batched writes) to avoid latency; analyze via Hadoop/Spark.  
- **Trade-offs**: Unused tokens from crashed instances are acceptable; asynchronous analytics may lose data but prioritizes latency.  
- **Storage**: Cassandra preferred for scalability; sharded MySQL is a viable alternative.