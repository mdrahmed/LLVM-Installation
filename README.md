# LLVM-Installation

##**Installing latest LLVM by cloning:**
```
git clone https://github.com/llvm/llvm-project.git
cd llvm-project
mkdir build
cd build
cmake -G Ninja -DLLVM_ENABLE_RTTI=ON -DLLVM_ENABLE_EH=ON -DBUILD_SHARED_LIBS=ON -DCMAKE_BUILD_TYPE=Release -DLLVM_TARGETS_TO_BUILD=X86 -DLLVM_ENABLE_ASSERTIONS=ON -DLLVM_ENABLE_PROJECTS="llvm;clang" ../llvm
ninja
sudo ninja install 
```

This will install latest LLVM.

After this, make a C file and generate ll file using following cmd,
```/home/raihan/llvm-project/build/bin/clang -O0 -S -emit-llvm input.c -o run.ll```

If -O1 instead of -O0 then it works fine in clang like following,
```clang -O1 -emit-llvm input.c -S -o out.ll``` > can also add -S

Then run this particular opt cmd to run the ll files,
```/home/raihan/llvm-project/build/bin/opt -load /home/raihan/llvm-project/build/lib/LLVMMyHello.so -myhello in.ll```

Run it after disabling new-pass-manager,
```/home/raihan/llvm-project/build/bin/opt -load /home/raihan/llvm-project/build/lib/LLVMMyHello.so -enable-new-pm=0 -myhello in.ll```

2nd Method,

```
git clone https://github.com/llvm/llvm-project.git
mkdir build
cd build
cmake -G Ninja ../llvm -DLLVM_TARGETS_TO_BUILD=X86 -DCMAKE_BUILD_TYPE=Release -DLLVM_ENABLE_PROJECTS=clang
ninja
```


##**Installing LLVM-14 or lower version by cloning:**
Choose the [llvm-version you want to install.](https://releases.llvm.org/download.html)
Then go to that particular page and download specifically this file which says: `llvm-project-14.0.6.src.tar.xz`

Then just simply go through the general steps like following:
```
```
git clone https://github.com/llvm/llvm-project.git
cd llvm-project
mkdir build
cd build
cmake -G Ninja -DLLVM_ENABLE_RTTI=ON -DLLVM_ENABLE_EH=ON -DBUILD_SHARED_LIBS=ON -DCMAKE_BUILD_TYPE=Release -DLLVM_TARGETS_TO_BUILD=X86 -DLLVM_ENABLE_ASSERTIONS=ON -DLLVM_ENABLE_PROJECTS="llvm;clang" ../llvm
ninja
```

Now, if you run `sudo ninja install` then it will add it to the path but if there is already another llvm present in path then it will collide with the new llvm.

