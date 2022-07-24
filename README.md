# Testing AWS Lambda Custom Rust Runtime
As far as I understand AWS is kind of supporting Rust as a development environment. When creating a Lambda within AWS you can't select a Rust Runtime directly like you're able to do for Python, Node, Ruby and Java. Instead you need to select a custom architecture and provide the runtime yourself. You can do this by "cross-compiling" the (unix) runtime environment into the Lambda function. Support for "x86_64-unknown-linux-musl" or "aarch64-unknown-linux-gnu" when targeting for a graviton supported runtime.

Initially I used Rust and Cargo from my distributions repository, which is advantageous from a management perspective. Then enforcing a musl target (provideing a static-linked blob) provided issues. To prevent mixups off multiple package managers (dnf and rustup), rust and cargo got de-installed and re-installed using the plain guidelines in the ![rust-book](https://doc.rust-lang.org/book/) . This provided a user-based install instead of the system-based install dnf used to provide.

After this the Lambda runs as expected.


