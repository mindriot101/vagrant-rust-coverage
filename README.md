# vagrant-rust-coverage
An example vagrant box for computing rust code coverage

## Set up

Copy the files from this repo into your rust code, then run the following:

```sh
cargo clean
vagrant up
vagrant ssh
for file in target/debug/-*[^\.d]; do
    mkdir -p "target/cov/$(basename $file)"
    kcov --exclude-pattern=/.cargo,/usr/lib --verify "target/cov/$(basename $file)" "$file"
done
```
