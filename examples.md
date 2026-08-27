# Examples

## Basic Usage

Initializing handles, inspecting the index and generation, and performing null checks:

```clojure
(use Handle)

(deftype Entity [])

(defn main []
  (let [h (Handle.init 10un 1un)]
    (do
      (IO.println &(str (Handle.index &h)))      ; 10
      (IO.println &(str (Handle.generation &h))) ; 1
      (IO.println &(str (Handle.not-null? &h))))))  ; true
```
