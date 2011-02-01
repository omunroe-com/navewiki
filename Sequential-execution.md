  Use of [creationix](https://github.com/creationix) [Step](https://github.com/creationix/step) library to control the execution flow in case of deeply nested callbacks may be difficult in coffee. `Step()` treats non-undefined values returned from steps as immediate (sync) result for the subsequent callback. Since coffee treats anything as expression, and implicit values are often returned from functions, subtle and hard to track logic errors may occur.

In particular, one must ensure `undefined` is returned from async steps.

In my pattern I try to not `throw` too much, so I must write such ugly (and not coffee-y) constructs:
    if err
        next err
        return

instead of beautiful
    return next err if err


  Another issue with `Step()` is that is completely spoils `@` (it's set to point to the next step), while it's feasible to have kinda "context" object available in steps as `@`.

Thus, assuming that, and that sync functions are rarely used in `Step()` (and can be easily mimicked as `next null, immediate-result`, if needed), wrote a barebone analog called `Next`:

    Next = (context, steps...) ->
    	next = (err, result) ->
    		throw err if not steps.length and err
    		fn = steps.shift()
    		try
    			fn.call context, err, result, next
    		catch err
    			next err
    		return
    	next()

Below is example:

    exec = () -> Next {foo: 'bar'},
    	(err, result, next) ->
    		console.log 'first', arguments
    		return next err if err
    		throw 'Catch me1!'
    		next 'err1', 'res1'
    	(err, result, next) ->
    		console.log 'second', arguments
    		return next err if err
    		next 'err2', 'res2'
    	(err, result, next) ->
    		console.log 'third', arguments
    		return next err if err
    		next 'err3', 'res3'

    try
    	exec()
    catch err
    	console.log 'CAUGHT', err

Feedback and critisism is welcome.


Have fun!

--Vladimir Dronnikov
