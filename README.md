# bookdown-collect-examples
Create collections of example chunks by type

The `collection.Rmd` file can be added to a bookdown book to collect example chunks by type.

For a book that has the following structure,
```
- Topic A
    - Theorem
    - Example Type 1
- Topic B
    - Example Type 1
    - Example Type 2
- Topic C
    - Example Type 2
```

You can create a collection page with examples organized by type:
```
- Example Collection
    - Example Type 1
        - From Topic A
        - From Topic B
    - Example Type 2
        - From Topic B
        - From Topic C
```

If the `collection.Rmd` is added to the end of the book in the `_bookdown.yml`, the book will have the following structure:
```
- Topic A
    - Theorem
    - Example Type 1
- Topic B
    - Example Type 1
    - Example Type 2
- Topic C
    - Example Type 2
- Example Collection
    - Example Type 1
        - From Topic A
        - From Topic B
    - Example Type 2
        - From Topic B
        - From Topic C
```

If the example chunks are labeled as `example-type1-topic-a`, `example-type1-topic-b`, `example-type2-topic-b` and `example-type2-topic-c`, the `example_types` vector should be specifed in this way:

```r
example_types <- c("example-type1", "example-type2")
```

If the chunks are labeled differently, the `startsWith` function may need to be replaced with a different function such as `endsWith`.

The block chunks need to be manually added for each of the example tyes in `collection.Rmd`:
<pre>
### `r example_types[[1]]`
```{block, ref.label=filtered_labs[[1]]}
```
</pre>
Change the number each time you add an example type.

In each of the example chunks, the example number should be added:
<pre>
```{example exm:example-type1-type-a}
\@ref(exm:example-type1-type-a)
Example Here
```
</pre>
