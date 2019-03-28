Install a JS library like jQuery
--------------------------------

Find the URL to jQuery at https://code.jquery.com/

```
<html>
    <head>
        <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    </head>
</html>
```

Apply click event that changes background style
-----------------------------------------------

```
<html>
    <head>
        <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    </head>
    <body>
        <button id="click_me">Make red background</button>
        <script>
            $('#click_me').on('click', function() {
                $('body').css('background-color', 'red');
            });
        </script>
    </body>
</html>
```
