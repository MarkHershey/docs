# Demo Page for MkDocs Material

## Text Formatting 

- **Bold**
- ~~Strikethrough~~
- *Italic*
- ==Highlight==

## MarkDown Table

| Method      | Description                          |
| :---------: | :----------------------------------: |
| `GET`       | :material-check:     Fetch resource  |
| `PUT`       | :material-check-all: Update resource |
| `DELETE`    | :material-close:     Delete resource |

## Admonitions

!!! note
    This is an Admonition with default header

!!! note ""
    This is an Admonition with no header


!!! note "Admonition"
    This is an Admonition with customised-text header


??? note "Collapsible Admonition"
    This is an Collapsible Admonition with customised-text header

    ``` python
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]
    ```

    Nunc eu odio eleifend, blandit leo a, volutpat sapien. Phasellus posuere in
    sem ut cursus. Nullam sit amet tincidunt ipsum, sit amet elementum turpis.
    Etiam ipsum quam, mattis in purus vitae, lacinia fermentum enim.

!!! tldr
    Other types of Admonitions

!!! info
    Other types of Admonitions

!!! tip
    Other types of Admonitions

!!! success
    Other types of Admonitions

!!! question
    Other types of Admonitions

!!! warning
    Other types of Admonitions

!!! failure
    Other types of Admonitions

## Code Blocks

Basic Code Block

``` python
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

Code Block with Line Number starting at 1

``` python linenums="1"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

Code Block with Line Numbers starting at 6 and Highlighted lines

``` python linenums="6" hl_lines="2 3"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

Multiple-language Tabs

=== "C"

    ``` c linenums="1"
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"

    ``` c++ linenums="1"
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```

=== "Java"

    ``` java linenums="1"
    class HelloWorld {
        public static void main(String[] args) {
            System.out.println("Hello, World!"); 
        }
    }
    ```

=== "Python"

    ``` python linenums="1"
    def main():
        print("Hello world!")
    ```

=== "Go"

    ``` go linenums="1"
    package main

    import "fmt"
    func main() {
        fmt.Println("hello world")
    }
    ```

## Math Formulas using LaTeX

- LateX Reference: [LaTeX for Undergrads Math](http://tug.ctan.org/info/undergradmath/undergradmath.pdf)

!!! example ""

    $$X = \sum_{i=0}^k d^k =\frac{1 - d^{k+1}}{1-d}$$
    
    $$X(1-d) = 1 - d^{k+1}$$

    $$1 - X(1-d) = d^{k+1}$$

    $$1 - X + dX = d^{k+1}$$

    $${k+1} = \log_d (1 - X + dX)$$

    $$k = \log_d (1 - X + dX) - 1$$


## Images

Just use HTML instead of MarkDown syntax for fine control over dimensions and margins.

<figure>
  <img src="https://dummyimage.com/600x400/eee/aaa" style="max-height:200px;max-width:400px;margin-top:5px;margin-bottom:5px" />
  <figcaption>Centered image with caption</figcaption>
</figure>

---

Complete Documentation: <https://squidfunk.github.io/mkdocs-material/reference/abbreviations/>