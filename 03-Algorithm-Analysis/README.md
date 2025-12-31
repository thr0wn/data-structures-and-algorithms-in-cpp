[![](https://img.shields.io/badge/c++-black?logo=c++&style=for-the-badge)](https://learnxinyminutes.com/c++/)

## Algorithm analysis
Here is implementation of the following algorithms:
- Max Sub Sequence Sum
- Binary Search
- Euclid's Greatest Common Divisor
- Recursive exponentiation

### Build
```shell
export CC=/usr/bin/gcc
export CXX=/usr/bin/g++
cmake -S . -B ./build
cmake --build build
```

### Run
```shell
./build/test-max-sum
./build/test-binary-search
./build/test-euclid
./build/test-exponentiation
```
