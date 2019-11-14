# Comments

* Prefer line comments to block comments (`//` or `///` to `/* ... */` or `//* ... */`).
* For module-level items, use doc comments, never regular comments (`///` over `//`).
* Use `//!` for module level documentation only.
* The first line of a doc comment should be a short and useful summary.
* Do not write comments which do not add information, e.g., `Gets a Foo from self` on `get_foo`. Not everything needs a comment.
* It can be very useful to add long comments to a module, rather than lots of short comments to each function, to give an idea of the core concepts for a module.
* Place the single-line and block comment above the code it’s annotating.
* Wrap long lines of comments at 80 or 100 characters.
* Document why a function might panic.
* Document any unsafe code.
* Do not commit commented out code.


### Rationale

* Consistency with the ecosystem and C/C++ code.
* IDEs display doc comments as hints, but not regular comments
* Some tools preference the first line of a doc comment.
* Existing guidelines:
  - [TiKV guidelines](https://github.com/tikv/tikv/blob/master/CODE_COMMENT_STYLE.md)
  - The Rust book: [Making Useful Documentation Comments](https://doc.rust-lang.org/book/ch14-02-publishing-to-crates-io.html#making-useful-documentation-comments)
  - [RFC 1574](https://github.com/rust-lang/rfcs/blob/master/text/1574-more-api-documentation-conventions.md)


## Where/When to comment?

Write a comment where/when there is context that is missing from the code or is hard to deduce from the code. Specifically, use a comment:

- For important code
- For obscure code
- For tricky or interesting code
- For a complex code block
- If a bug exists in the code but you cannot fix it or you just want to ignore it for the moment
- If the code is not optimal but you don’t have a smarter way now
- To remind yourself or others of missing functionality or upcoming requirements not present in the code

The last three should be highlighted with `FIXME` (prefer that to `TODO` so that developers can use `TODO` for temporary reminders). In most cases, you should file an issue and add it to the comment: `FIXME(#1234): a summary of the issue`.

Prefer to write about *why* something is done, rather than *what* and *how* (which can be gleaned from the code), unless the code is complicated. It is very useful to write about trade-offs or performance issues which are not clear from the code.


## Language for a good comment

- Words
    
    - Use **American English** rather than British English.
        
        - color, canceling, synchronize     (Good)
        - colour, cancelling, synchronise   (Bad)
    
    - Use correct spelling.

    - Use **standard or official capitalization**.
        
        - TiKV, TiDB-Binlog, Region, gRPC, RocksDB, GC, k8s, [mydumper](https://github.com/maxbube/mydumper), [Prometheus Pushgateway](https://github.com/prometheus/pushgateway)   (Good)
        - Tikv, TiDB Binlog, region, grpc, rocksdb, gc, k8S, MyDumper, Prometheus PushGateway   (Bad)

    - Use words and expressions consistently.
        
        - "dead link" vs. "broken link" (Only one of them can appear in a single document.)
    
    - Do not use lengthy compound words.

    - Do not abbreviate unless it is necessary (for readability purposes).

    - "we" should be used only when it means the code writer *and* the reader.

- Sentence

    - Use standard grammar and correct punctuation.
    - Use relatively short sentences.

- For each comment, capitalize the first letter and end the sentence with a period.

- When used for description, comments should be **descriptive** rather than **imperative**.

    - Opens the file   (Good)
    - Open the file    (Bad)

- Use "this" instead of "the" to refer to the current thing.
    
    - Gets the toolkit for this component   (Good)
    - Gets the toolkit for the component    (Bad)

- Markdown format is allowed.

- Use relative URLs when appropriate for Rustdoc links.


## Tips

- Comment code while writing it.
- Do not assume the code is self-evident.
- Avoid unnecessary comments for simple code.
- Write comments as if they were for you.
- Make sure the comment is up-to-date.
- Make sure you keep comments up to date when you edit code.
- Let the code speak for itself.


## Why does a good comment matter?

- To speed up the reviewing process
- To help maintain the code
- To improve the API document readability
- To improve the development efficiency of the whole team