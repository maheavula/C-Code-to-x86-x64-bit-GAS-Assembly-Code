# Programming Syntaxes: C, Java, Python

# C, Java, and Python Syntax Comparison

## Variables
| Concept  | C Syntax                  | Java Syntax                  | Python Syntax               |
|----------|---------------------------|------------------------------|-----------------------------|
| Variable Declaration | `int a = 5;`     | `int a = 5;`                | `a = 5`                     |
| Variable Initialization | `int a = 5;` | `int a = 5;`                | `a = 5`                     |

## Data Types
| Concept  | C Syntax                  | Java Syntax                  | Python Syntax               |
|----------|---------------------------|------------------------------|-----------------------------|
| Integer  | `int a;`                  | `int a;`                     | `a = 5`                     |
| Float    | `float b;`                | `float b;`                   | `b = 5.0`                   |

## Constants
| Concept  | C Syntax                  | Java Syntax                  | Python Syntax               |
|----------|---------------------------|------------------------------|-----------------------------|
| Constant | `const int a = 10;`       | `final int a = 10;`          | `a = 10`                    |

## Operators
| Concept       | C Syntax               | Java Syntax                  | Python Syntax               |
|---------------|------------------------|------------------------------|-----------------------------|
| Arithmetic    | `a + b`                | `a + b`                      | `a + b`                     |
| Comparison    | `a == b`               | `a == b`                     | `a == b`                    |

## Booleans
| Concept  | C Syntax                  | Java Syntax                  | Python Syntax               |
|----------|---------------------------|------------------------------|-----------------------------|
| Boolean  | `int a = 1;` (0 or 1)     | `boolean a = true;`          | `a = True`                  |

## If...Else
| Concept     | C Syntax                      | Java Syntax                        | Python Syntax                 |
|-------------|-------------------------------|------------------------------------|-------------------------------|
| If Statement| `if (a > b) { /*...*/ }`      | `if (a > b) { /*...*/ }`           | `if a > b:`                   |
| Else        | `else { /*...*/ }`            | `else { /*...*/ }`                 | `else:`                       |

## Switch
| Concept    | C Syntax                           | Java Syntax                              | Python Syntax                 |
|------------|------------------------------------|------------------------------------------|-------------------------------|
| Switch     | `switch (a) { case 1: /*...*/ }`   | `switch (a) { case 1: /*...*/ }`         | `# Python does not have switch`

## Loops
| Concept      | C Syntax                    | Java Syntax                      | Python Syntax                 |
|--------------|-----------------------------|----------------------------------|-------------------------------|
| While Loop   | `while (a < b) { /*...*/ }` | `while (a < b) { /*...*/ }`      | `while a < b:`                |
| For Loop     | `for (i = 0; i < n; i++)`   | `for (int i = 0; i < n; i++)`    | `for i in range(n):`          |
| Break/Continue| `break;` / `continue;`      | `break;` / `continue;`           | `break` / `continue`          |

## Arrays
| Concept    | C Syntax                          | Java Syntax                          | Python Syntax                 |
|------------|-----------------------------------|--------------------------------------|-------------------------------|
| Array      | `int arr[5];`                     | `int[] arr = new int[5];`            | `arr = [0]*5`                 |

## Strings
| Concept    | C Syntax                          | Java Syntax                          | Python Syntax                 |
|------------|-----------------------------------|--------------------------------------|-------------------------------|
| String     | `char str[] = "Hello";`           | `String str = "Hello";`              | `str = "Hello"`               |

## User Input
| Concept    | C Syntax                          | Java Syntax                          | Python Syntax                 |
|------------|-----------------------------------|--------------------------------------|-------------------------------|
| Input      | `scanf("%d", &a);`                | `Scanner sc = new Scanner(System.in); int a = sc.nextInt();` | `a = input()`                 |

## Memory Address
| Concept    | C Syntax                          | Java Syntax                          | Python Syntax                 |
|------------|-----------------------------------|--------------------------------------|-------------------------------|
| Address    | `&a`                              | N/A                                  | `id(a)`                       |

## Pointers
| Concept    | C Syntax                          | Java Syntax                          | Python Syntax                 |
|------------|-----------------------------------|--------------------------------------|-------------------------------|
| Pointer    | `int *p = &a;`                    | N/A                                  | N/A                           |

## Functions
| Concept           | C Syntax                                  | Java Syntax                              | Python Syntax                 |
|-------------------|-------------------------------------------|------------------------------------------|-------------------------------|
| Function Definition| `int func(int a) { return a; }`          | `int func(int a) { return a; }`          | `def func(a): return a`       |
| Function Parameters| `int func(int a, int b)`                 | `int func(int a, int b)`                 | `def func(a, b)`              |
| Scope             | Local and Global                          | Local and Global                          | Local and Global              |
| Declaration       | `int func(int);`                          | Method signature in class                 | Function declaration          |
| Recursion         | Supported                                 | Supported                                 | Supported                     |
| Math Functions    | `#include <math.h>`                       | `import java.lang.Math;`                  | `import math`                 |

## Files
| Concept         | C Syntax                                    | Java Syntax                              | Python Syntax                 |
|-----------------|---------------------------------------------|------------------------------------------|-------------------------------|
| Create Files    | `FILE *fp = fopen("file.txt", "w");`        | `File file = new File("file.txt");`      | `file = open("file.txt", "w")`|
| Write To Files  | `fprintf(fp, "Hello");`                     | `PrintWriter out = new PrintWriter(file); out.print("Hello");` | `file.write("Hello")`         |
| Read Files      | `fscanf(fp, "%s", str);`                    | `Scanner sc = new Scanner(file); sc.next();` | `file.read()`                 |

## Structures
| Concept         | C Syntax                                    | Java Syntax                              | Python Syntax                 |
|-----------------|---------------------------------------------|------------------------------------------|-------------------------------|
| Structures      | `struct Person { int age; char name[50]; };`| `class Person { int age; String name; }` | `class Person: def __init__(self, age, name): self.age = age; self.name = name` |

