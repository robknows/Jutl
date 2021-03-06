# JTests
Some explicit testing functions for J

# Usage for testing functions: found in JTests.ijs

If I have some code I want to test such as:

```J
stack =: 0
push =: 3 : 'stack =: y , stack' 	NB. Pushes items of y onto the stack
drop =: 3 : 'stack =: y }. stack' 	NB. Drops y items from the stack
```

I can test it by writing a test, which is a noun, as indicated by the first "0" in 0 : 0:


```J
canPushToStack =: 0 : 0
  stack =: 0            NB. reset the stack
  push 1                NB. push a 1 onto the stack
  stack shouldEqual 1 0 NB. make the appropriate assertion
)
```

To compute the result of the test, I can call the function runTests:

`runTests canPushToStack`

If I have many other tests, one of which is called canDropItemsOffStack, I can run that at the same time by boxing the test definitions:

`runTests canPushToStack ; canDropItemsOffStack ; blah ; blah2 ; ...`

Note that the results of the test are not evaluated until they are called upon by the runTests function.
