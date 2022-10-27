
## task 1: compile the compiler and link it

in the container terminal session

- [ ] build it
```bash
cd /tmp/workshop-sources/jdk
make jdk
```

- [ ] link it
```bash
jenv add build/linux-x86_64-server-release/jdk
```

- [ ] test it on our maven project
```bash
cd /tmp/workshop-sources/openjdk-compiler-workshops/compiler-lint-options
mvn compile -P lint-all # should fail build with redundant cast error
mvn compile -P lint-everything # should fail build with error: invalid flag: -Xlint:everything

mvn compile exec:java # see runtime errors in action
mvn clean # to trigger lint errors on subsequent compiles
```

## task 2 : lint everything

The purpose of this task is to mirror the behaviour of `-Xlint:all`, so we will be navigating around to see
how `-Xlint:all` is implemented under the hood

- [ ] add a new lint option "everything" that operates the same as "all"

## task 3 : lint bad cast - part one

The purpose of this task is to add a new lint option, something similar to `-Xlint:cast`,  we will however make it
emit a warning when it is enabled. We will build out the actual logic in a later task

- [ ] add a new lint option "bad-cast" that always emits a warning when enabled, we can enable it with `-Xlint:bad-cast`
- [ ] test it on our maven project (notice the maven profile configuration)

```bash
cd /tmp/workshop-sources/openjdk-compiler-workshops/compiler-lint-options
mvn compile -P lint-bad-cast
```

## task 4 : lint bad cast - part two

The purpose of this task is to inspect Java compiler types to build out the logic for determining an incompatible cast
in a chain of casts.

- [ ] update "bad-cast" implementation to inspect cast chain for incompatibilities
- [ ] test it on our maven project (notice the maven profile configuration)

```bash
cd /tmp/workshop-sources/openjdk-compiler-workshops/compiler-lint-options
mvn compile -P lint-bad-cast
```
