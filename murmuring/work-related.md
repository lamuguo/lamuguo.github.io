# Tech Related Hints

## STM32 / Coding and related
### Checklist before submitting...
- Clean up logs (debug! / info!)
- cargo.toml dependencies
- Remove uartwrapper used in ctl200-demo
- remove string in error. Provide more error types.
- act run workflows

### 连接常见错误
- baud-rate
- 选择器是否接对

### Frequently used git commands

```shell
git log --pretty=format:"%an - %ad - %s" --date=short
git push origin --delete <branch-name>
```

### Rust coverage

```shell
cargo install cargo-tarpaulin
cargo tarpaulin --out Html
```

### Defmt
#### How to debug defmt
编译完之后nm看看里面有没有defmt对应的信息就是了。

待解决问题：
- defmt如果没有debug info，就是没句话在哪里log的？
- defmt log格式定义，譬如我不想要多打一行看它在哪里。

### Crash in STM32
The most common bug that causes everything to stop working is a stack overflow. (For example, passing a large object by value, or putting a large object on the stack instead of lazy static.) The default stack size is very small.

The other common bug is a panic, and not having the panic handler set correctly. 

And a third common thing is assigning the wrong DMA channel to the wrong memory region. Not all DMA channels can work with all memory segments in the H7.

看内存分配：
arm-none-eabi-nm -CSn target/thumbv7em-none-eabi/debug/examples/ctl200-demo

https://classpert.com/classpertx/courses/making-embedded-systems/cohort

我们可以看defmt的内存分配1024 / 65536的时候各自不同，用build出来nm看。

heapless时候的stack生长

0.012390 INFO 1 | Current SP: 0x2400F91C
0.022857 INFO 2 | Current SP: 0x2400F91C
0.125610 INFO 8 | Current SP: 0x2400F91C

https://crates.io/crates/lexical-parse-float

### How to log in a simple test case in Rust
没搞定怎么弄log.info，但是可以搞定println!()

        println!("11111: status: '{}'", format_fixed!("{}", status).as_str());

用下面的命令就可以打印出来
RUST_LOG=debug cargo test --package ferox drivers::koheron::ctl200::tests::test_board_status_display -- --nocapture

后面都可以了，只要正确Init了env_logger就可以。

## VA Related

### How Iodine clock works?
- https://www.nist.gov/atomic-clocks/optical-clocks-future-time
- https://eventhelix.com/rust/rust-to-assembly-async-await/
- https://en.wikipedia.org/wiki/Hyperfine_structure