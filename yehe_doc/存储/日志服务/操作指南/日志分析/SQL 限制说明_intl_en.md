| Metric | Limit | Remarks                                                       |
| ---------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Maximum length of a single statistical field (Value) | The maximum length of a single statistical field (Value) is 32 KB, the part beyond which will be truncated. | The truncation occurs when the search module is stored. |
| Number of non-cluster analysis results (excluding GROUP BY clauses) | Each analysis returns up to 1,000 results.                              | Default: 100; Maximum: 1,000                                 |
| Number of cluster analysis results (including GROUP BY clauses) | Each analysis returns up to 100 results.                              | Default: 100; Maximum: 1,000                                 |
| ORDER BY clause limit                        | The ORDER BY operation is not supported for fields that have been computed using one of the functions “round”, “sqrt”, “abs”, “power”, and “floor”, or one of the four fundamental operations. |                                         —                     |
