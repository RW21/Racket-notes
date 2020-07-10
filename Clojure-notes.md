## Control flow

- `if`
- `when`
  - Doesn't need else.
  
- `nil?`

## Data structures

- `[]` vectors

### Maps

- `{}`

```clojure
{:first-name "Charlie"
:last-name "Who"}

(hash-map :a 1 :b 2)
```

- `get` to retrieve.
- `get-in` to retrieve in nested.

### Keywords

`:34`, `:rumple`

- Keywords can be used as a function for lookup.

### Sets

#### Hash sets

- Same as sets in Python.
- `#{}`

## Functions

### Defining functions

```clojure
(defn hello
	[first last]
	(str "hello" first last))
```

Arity overloading:

```clojure
(defn multi-arity
  ;; 3-arity arguments and body
  ([first-arg second-arg third-arg]
     (do-things first-arg second-arg third-arg))
  ;; 2-arity arguments and body
  ([first-arg second-arg]
     (do-things first-arg second-arg))
  ;; 1-arity arguments and body
  ([first-arg]
     (do-things first-arg)))
```

Something like `*args`

```clojure
(defn codger
   [& whippersnappers]
  (map codger-communication whippersnappers))
```


