### List Loops

- `map`
- `andmap`, `ormap`
- `filter`
- `foldl`, `foldr`

```racket
(foldl (lambda (elem v)
	(+ v (* elem elem)))
	0
	'(1 2 3))
; 14

(define (my-length lst)
	(cond
		[(empty? lst) 0]
		[else (+ 1 (my-length (rest lst)))]))
		
(define (my-map f lst)
	(cond
		[(empty? lst) empty]
		[else (cons (f (first lst)) (my-map f (rest lst)))]))
		
		
; tail recursion
(define (my-length1 lst)
	(define (iter lst len)
		(cond
			[(empty? lst) len]
			[else (iter (rest lst) (+ len 1))]))
	(iter lst 0))
	
(define (remove-dups l)
	(cond 
	[(empty? l) empty]
	[(empty? (rest l)) l]
	[else
		(let ([i (first l)])
			(if (equal? i (first (rest l)))
				(remove-dups (rest l))
				(cons i (remove-dups (rest l)))))]))
```


## Datatypes

### Symbols

- An atomic value.

### Vectors

Unlike a list, vectors support constant-time access and update of its elements.

```racket
#("a" "b" "c")

#(vector-ref #(1 2 3) 1)
```

### Hash Tables

Note there are immutable and mutable hash tables.

```racket
(define ht (make-hash))
(hash-set! ht "apple" '(red round))
(hash-ref ht "apple")
```

## Expressions and Definitions

### `apply` Function

```racket
(define (avg lst)
	(/ (apply + lst) (length lst)))
```

### Lambda

```racket
(define max-mag
  (lambda nums
      (apply max (map magnitude nums))))
	  
(define max-mag1
	(lambda (num . nums)
		(apply max (map magnitude (cons num nums)))))
		
; optional arguments
(define greet
	(lambda (given [surname "Smith"])
		(string-append "Hello, " given " " surname)))
		
(define (firsts_ lst)
  (map (lambda (a) (car a)) lst))
```

### Define

```racket
(define make-add-suffix
	(lambda (s2)
		lambda(s) (string-append s s2)))

; > ((make-add-suffix "!") "hello)
; "hello!"

(define ( make-add-suffix s )
	(lambda (s) (string-append s s2)))
```

- `values` to return multiple values.
  - `define-values` to bind them to multiple identifiers.
  
### Local Binding

```racket
(let ([a 1]
	[b 2]
	[c 3])
	(list a b c))

;'(1 2 3)

```

### Sequencing

```racket
(define (print-triangle height)
	(if (zero? height)
		(void)
		(begin
			(display (make-string height #\*))
			(newline)
			(print-traingle (sub1 height)))))
```

- `begin0`
- `when` and `unless`

### Conditionals

```racket


## Structure Types

```racket
