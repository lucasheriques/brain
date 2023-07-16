# Book Summary: The Effective Engineer

![rw-book-cover](https://readwise-assets.s3.amazonaws.com/static/images/article0.00998d930354.png)

## Metadata
- Author: [[Joe Schafer]]
- Full Title: Book Summary: The Effective Engineer
- Category: #articles
- URL: https://blog.d46.us/effective-eng-summary/

## Highlights
- Focus on High-Leverage Activities
  Lau’s central premise is to increase leverage, which he defines as follows:
  Leverage=Impact ProducedTime Invested \text{Leverage} = \frac{\text{Impact Produced}}{\text{Time Invested}} ([View Highlight](https://read.readwise.io/read/01h2er0ntehzfb7t9d34ad79cs))
- learning is a high-leverage activity due to its exponential growth. As engineers build their base of knowledge, the combination of learned skills increases the areas to which an engineer can contribute. The increased depth and breadth an engineer can contribute to making learning a high-leverage activity. An engineer should regularly invest in active learning. ([View Highlight](https://read.readwise.io/read/01h2er5vty0bd8gcmyw6kv5bw2))
    - Note: potential avenues for learning: study core abstractions, taking classes on broad topics, writing more code, mastering a programming language, get the harshest code reviews, pick diverse projects, work with people with more seniority, jump into code fearlessly
- Instead, identify a *few goals* and conduct a pairwise comparison between goals, focusing on items that directly produce value. ([View Highlight](https://read.readwise.io/read/01h2et1a3kwn9hvq1b93pvp5xx))
- Effective engineers invest in tools to increase efficiency. Data from Facebook shows that engineers who invest in their tools are more effective. Tools can range from shell scripts up to full automation platforms for testing and deployment. In addition to engineering efficiencies, Lau reminds readers to examine non-engineering bottlenecks like meetings, long-winded standups, and one-on-one meetings. ([View Highlight](https://read.readwise.io/read/01h2et3qaw5vnejfat1yr2b8rp))
- good metric possesses the following qualities:
  • Maximizes impact.
  • Actionable. The movement of a metric is causally explained by something the engineering team did.
  • Responsive. The metric updates quickly enough to provide timely feedback.
  • Robust. The metric isn’t overly influenced by external factors. ([View Highlight](https://read.readwise.io/read/01h2et69e0n5jtrmqb6sbfp84z))
- The following times typify the most common examples of times in software.
  Access Type
  Latency (ns)
  Latency (ms)
  L1 cache reference
  0.5
  0.0000005
  Branch mispredict
  5
  0.000005
  L2 cache reference
  7
  0.000007
  Mutex lock/unlock
  100
  0.00001
  Main memory reference
  100
  0.00001
  Compress 1K bytes with Snappy
  10,000
  0.01
  Send 2K bytes over 1Gbps network
  20,000
  0.02
  Read 1MB sequentially from memory
  250,000
  0.25
  Roundtrip within same datacenter
  500,000
  0.5
  Disk seek
  10,000,000
  10
  Read 1MB sequentially from network
  10,000,000
  10
  Read 1 MB sequentially from disk
  30,000,000
  30
  Roundtrip from CA to Netherlands
  150,000,000
  150 ([View Highlight](https://read.readwise.io/read/01h2ethmzbjb4s126j8qr2b3y7))
    - Note: To better grasp the vast time differences, if an L1 cache reference took one second, a round trip from CA to the Netherlands would take about ten years.
- analytics pipelines are not nearly as well tested as application code, so managers and engineers should be skeptical of data integrity. To restore confidence in analytics, create a pipeline with the following guidelines.
  • Log data liberally.
  • Build tools to iterate on data sooner.
  • Run end-to-end integration tests on analytics.
  • Examine collected data sooner.
  • Cross-validate by computing metrics in multiple ways.
  • When numbers look off, dig into the problem. ([View Highlight](https://read.readwise.io/read/01h2etg2ap38qetjg6t863tvww))
- Validate Your Ideas Early and Often
  Avoid investing time into products with an unknown chance of success. Work towards a minimum viable product (MVP), validated with a prototype, static site, or in [Dropbox’s case](https://news.ycombinator.com/item?id=8863), a video. After releasing an MVP, continuously validate with [A/B testing](https://en.wikipedia.org/wiki/A/B_testing). For A/B testing, hone in on differences that are high-leverage and of practical significance. At a startup’s scale, shades of blue are not usually significant. At Google’s scale, the right shade of blue might mean [millions of dollars](https://www.theguardian.com/technology/2014/feb/05/why-google-engineers-designers) of additional revenue. ([View Highlight](https://read.readwise.io/read/01h2etz1fq9vmk2mcfdskwggfq))
- When estimating projects, define specific goals and *measurable* milestones. Reduce risk early by tackling the riskiest areas first. Approach rewrites with extreme caution. ([View Highlight](https://read.readwise.io/read/01h2ev1ypy48ec1pqmyxxt20kp))
- “managing complexity is the primary goal of software construction.” ([View Highlight](https://read.readwise.io/read/01h2ev3tfcry5dztxjn8tme1ww))
- good abstractions should be:
  • Easy to learn.
  • Easy to use even without documentation.
  • Hard to misuse.
  • Sufficiently powerful to satisfy requirements.
  • Easy to extend.
  • Appropriate to the audience. ([View Highlight](https://read.readwise.io/read/01h2ev45fe5ngx0gpej5jvxjwp))
- embrace operation simplicity instead of new technologies. When reviewing designs, ask if this design is the simplest approach. Design technology to fail fast; the sooner a component fails the easier it is to debug. ([View Highlight](https://read.readwise.io/read/01h2ev564dw3f9bq01exgc2jj7))
- relentlessly automate mechanical tasks ([View Highlight](https://read.readwise.io/read/01h2evag1gxpwt3x7w35atvmwm))
- engineers should automate more but usually don’t because they don’t have time at the current moment ([View Highlight](https://read.readwise.io/read/01h2evakjvj4n04tqexn1fxjk2))
- The collective time saved by automation vastly exceeds the initial time commitment required to add automation. ([View Highlight](https://read.readwise.io/read/01h2evax202zy0077d5aag2e9s))
- following traits indicate a great engineering team:
  • Optimize for iteration speed.
  • Push relentlessly towards automation.
  • Build the right software abstractions.
  • Focus on high code quality by using code reviews.
  • Maintain a respectful work environment.
  • Build shared ownership of code.
  • Invest in automated testing.
  • Allot experimentation time, either through 20% time or hackathons.
  • Foster a culture of learning and continuous improvement.
  • Hire the best. ([View Highlight](https://read.readwise.io/read/01h2evcajq0w39f82h3x270byv))
