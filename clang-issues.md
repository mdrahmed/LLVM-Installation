# All issues while running `make` for `/LogPasses-new/FAVCIGVT*`

## iostream not found
`apt install libstdc++-12-dev` fixes this issue. Because the standard libraries of version 12 will be found by clang.

```
root@5d3c40bb818e:~/LogPasses-new/FAVCIGVT*# make
clang++-14 -o clientOrPublisher.ll -S -emit-llvm client_subscriber.cpp
client_subscriber.cpp:1:10: fatal error: 'iostream' file not found
#include <iostream>
         ^~~~~~~~~~
1 error generated.
```

Now, there can be some mqtt header related errors, [follow this doc.](https://docs.google.com/document/d/1NUTDBS5PnGsBR0BcgSc_4W4UopRmQgS1lQ7VCYrKe7s/edit)
