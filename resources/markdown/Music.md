
----

Music
=====


When you are modeling a problem of a sufficient level of complexity you will find
that your data-types often become recursive. One domain that sits roughly on this
threshold is music.

<!-- http://i824.photobucket.com/albums/zz163/Boysie8/Telecaster%20build/f-hole.jpg -->
<div class="center"> ![Music F-Hole](resources/images/f-hole.jpg) </div>

<div class="important">

Here is a small musical target-language:

~~~{data-language="haskell"}
data Music
  = A_ -- Underscore Represents a Flat
  | A
  | A' -- Prime represents a Sharp
       -- ... B, C, D, E, F, G ...
  | Sequence [Music]
  | Sharp Music
  | Longer Integer Music
  | Higher Integer Music
~~~

</div>

Certainly not comprehensive enough to write Beethoven's 5th Symphony,
but good enough for Baa Baa Black-Sheep.

~~~{data-language="haskell"}
intro  = Sequence [ C, C, G, G ]
run    = Sequence [ A, B, C, A ]
middle = Sequence [ F, F, E, E ]
run2   = Sequence [ D, C, D, E ]
baaBaa = Sequence [ Longer 2  intro
                  , Higher 12 run
                  , Longer 4  G
                  , Longer 2  middle
                  , run2
                  , Longer 4  C ]
~~~


In order to listen to this music, create a file with the following code:

~~~{data-language="haskell"}
import Midi
import qualified Data.ByteString as BS

main = BS.writeFile "baaBaa.mid" (make_music baaBaa)
~~~

```instruction
 
  
Write a melody using this language. Try to write and compose
functions, rather than declaring one big data-structure.

Why not try writing Beethoven's 5th Symphony after all?
```

```open
An open question:
  
What kinds of music is this language incapable of modeling?
How would you modify this language to be more inclusive?
```
