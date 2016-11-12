# Nanopass scheme compiler in scheme for x86

This is a scheme compiler for my study.
It runs on macOS only.

## Compile fib

```
$ gosh
gosh> (load "./compiler.scm")
gosh> (x86
        (cg-top
          (code-generation-form
            (immediate-literal-form
              (assignmentless-form
                (analyzed-form
                  (beta-reduce
                    (cps-form
                      (core-form
                        (local-form
                          (macroless-form
                            (append-library
                              '(letrec ((fib (lambda (n)
                                               (if (= n 0)
                                                   n
                                                   (if (= n 1)
                                                       n
                                                       (+ (fib (- n 1)) (fib (- n 2))))))))
                                 (fib 35))))))))))))))
$ ./a.out
9227465
```

# Run sample code

```
$ ./run samples/tinyrenderer.scm
```

# Run test code

```
$ ./runtests
```

## References

1. Summer Scheme Workshop; Compiling Scheme, http://www.cs.indiana.edu/eip/compile/
1. Ur-Scheme, http://www.canonical.org/~kragen/sw/urscheme/
1. An Incremental Approach to Compiler Construction, http://www.cs.indiana.edu/~aghuloum/
1. The 90 Minute Scheme to C compiler, http://www.iro.umontreal.ca/~boucherd/mslug/meetings/20041020/minutes-en.html
1. scheme -> LLVM, http://www.ida.liu.se/~tobnu/scheme2llvm/
1. 非決定的計算オペレータ amb の並列化, http://www.principia-m.com/ts/0127/index-jp.html
1. Tiny Renderer or how OpenGL works: software rendering in 500 lines of code, https://github.com/ssloy/tinyrenderer
