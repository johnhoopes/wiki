<!-- TITLE: Asm -->
<!-- SUBTITLE: A quick summary of Asm -->

# Running Shellcode in C
From: https://tuttlem.github.io/2017/10/28/executing-shellcode-in-c.html


```text
#include <stdio.h>

unsigned char code[] = "\xb8\x0a\x00\x00\x00\xc3";

int main(int argc, char **argv) {
  int foo_value = 0;

  int (*foo)() = (int(*)())code;
  foo_value = foo();

  printf("%d\n", foo_value);
}
```

Note you need two compiler flags for gcc
-z execstack and --fno-stack-protector. Without these our code will just segfault.

