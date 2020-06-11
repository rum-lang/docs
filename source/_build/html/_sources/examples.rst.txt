Examples
========

Hello, World!
--------------

.. code-block:: none
    :linenos:

    main = do
        printLn 'Hello, World!'

Arrays, for loops, and strings
---------------------------------

.. code-block:: none
    :linenos:

    main = do
        result =
            string::new
        nums =
            [0, 1, ..50]
        
        for num in nums do
            result.push string::interpolate(nums, ' ')
        
        printLn result

Fizz-Buzz (v1)
--------------

.. code-block:: none
    :linenos:

    fizzBuzz n = n
        | n % 15 is 0 => "FizzBuzz"
        | n % 3 is 0  => "Fizz"
        | n % 5 is 0  => "Buzz"
        | else        => n 

    main =
        printLn fizzBuzz [0..100]

Fizz-Buzz (v2)
--------------

.. code-block:: none
    :linenos:

    main =
        printLn n
            | n % 15 is 0 => "FizzBuzz"
            | n % 3 is 0  => "Fizz"
            | n % 5 is 0  => "Buzz"
            | else        => n 
          where
            n = [0..100]