
RoaringBitmap is a memory efficient, high performance compressed bitmap data structure. It is widely used in numerous big data and analytics softwares.

Ants Aasma discusses how RoaringBitmap was used to solve a very practical problem.

[Ants Aasma: Counting things at the speed of light with roaring bitmaps (PGConf.EU 2023)](https://www.youtube.com/watch?v=LM2VYmW0MjQ)<br>
PostgreSQL Europe<br>
Jan 9, 2024<br>

#### Use-Case:
1. Search through 100 million documents
2. Need accurate results
3. No false positives
4. Response time to be less than 2 seconds 😄


| **Solution** | **Time taken** |
|:---------------------------------|:-------------|
| Naive implementation - SQL query | ~ 32 seconds |
| RoaringBitmap based implementation :rocket: | < 1 second ! |


### References
- [pg_roaringbitmap](https://github.com/ChenHuajun/pg_roaringbitmap): [Chen Huajun](https://github.com/ChenHuajun)'s extension providing RoaringBitmap in Postgres
- [pgfaceting](https://github.com/cybertec-postgresql/pgfaceting): PostgreSQL extension to quickly calculate facet counts using pg_roaringbitmap
- [RoaringBitmap](https://github.com/RoaringBitmap/RoaringBitmap): [Prof. Daniel Lemire](http://lemire.me/en/)'s original implementation of RoaringBitmap
- [Ants Aasma](https://x.com/AntsAasma)
