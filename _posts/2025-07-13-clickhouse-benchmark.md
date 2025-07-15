# ClickBench: The ClickHouse Benchmark site - Some Observations

Some time ago, I learnt about [ClickBench](https://benchmark.clickhouse.com). Although, the title says "a Benchmark For **Analytical** DBMS", it also includes data for traditional RDBMS systems like [MySQL](https://www.mysql.com), [Postgres](https://www.postgresql.org/) etc.<br>

ClickHouse runs extensive benhmarks.<br>

- The best part is that all the results are freely available on [GitHub](https://github.com/ClickHouse/ClickBench) and
- The fun part is that you can use this website to compare results for any 2 or more products even other than ClickHouse !

Here's a snapshot of the homepage (dark-mode is enabled)<br>

![ClickBench Default view](/images/clickbench-20250626.png)

It looks impressive, but that's lot of information to digest and it certainly feels overwhelming ... :slightly_smiling_face:<br>

The webpage is divided into 3 sections:
1. Various Inputs (System, Type, Machine etc.)
2. A horizontal bar chart reporting the Relative times and
3. The Detailed Comparison table

After spending some time playing around, I realized that one can get lot more _meaningful_ information from this website by <ins>deselecting</ins> the defaults and instead, by choosing parameters that matter to you. e.g.<br>

Say, you want to do side-by-side comparison between ClickHouse and [TimescaleDB](https://www.tigerdata.com/) aka TigerData.

1. After selecting the following inputs,

![Inputs for comparing ClickHouse vs TimescaleDb](/images/clickhouse-timescale-input.png)

you get to see more of an ***Apples to Apples*** comparison as seen below.<br>

![Detailed Comparison between ClickHouse and TimescaleDB](/images/clickhouse-timescale-results.png)

Notice that both the runs were done on the same Amazon EC2 instance type: [c6a.4xlarge](https://aws-pricing.com/c6a.4xlarge.html) with 500 GB gp2.

2. If you click on the 'System & Machine' type in the 'Relative time' output, then it takes you to the corresponding results data on GitHub e.g. [ClickHouse (c6a.4xlarge, 500gb gp2)](https://github.com/ClickHouse/ClickBench/blob/main/clickhouse/results/c6a.4xlarge.json).<br>One of the benefits of visiting the GitHub page is that we get to see some additional information in the JSON output like cluster_size, tags, data size etc.

3. By howering the cursor on query ID, we also get to see the actual query that was run e.g.

![View the actual query](/images/detailed-comparison-query-20250626.png)

<br>

### Wish List

1. The benchmark site is kind of "hidden". Maybe, it should be listed in the drop down list from the Resources tab on the ClickHouse homepage.
2. It would be helpful to know the product versions that were used for benchmarking.<br>
   Looks like as of today, the version information is available only for [ClickHouse](https://benchmark.clickhouse.com/versions/) !<br>
   - I believe, the existing ClickHouse users would want to know what changes - new features, bug-fixes are incorporated in a specific release.<br>This information is available from the main website, but a link to the Release Notes would make it easier to take a peek.

3. An intelligent input selection available via drop down menu that filters out all the permutations that are not relevant.<br>This would save some time for the end-users, make it easy to grok the information and as a side benefit, would also free up some space in the top portion of the website.
