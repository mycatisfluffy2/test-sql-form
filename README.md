```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome to pyEstate</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <script src="https://cdn.jsdelivr.net/npm/tinymce@5.10.2/tinymce.min.js" referrerpolicy="origin"></script>
    <!-- <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script> -->
    <script>
        tinymce.init({
            selector: '.editor',
            menubar: false,
            plugins: 'advlist autolink lists link charmap print preview anchor textcolor',
            toolbar: 'undo redo | formatselect | bold italic backcolor | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | removeformat'
        });
    </script>
    <link rel="stylesheet" href="{{ url_for('static', filename='styles.css') }}">
</head>
<body>
    <form action="/" method="post">
            <div class="container">
                <div class="column">
                    {% for i in range(8) %}
                    <input type="text" name="data_input_{{ i }}" placeholder="Data" class="form-control">
                    {% endfor %}
                </div>
                <div class="column">
                    {% for i in range(8) %}
                    <input type="text" name="column_input_{{ i }}" placeholder="Column Name" class="form-control">
                    {% endfor %}
                </div>
                <div class="row" class="content-sizing" style="margin-top: 5px;">
                    <input type="text" name="table_name" placeholder="Table Name" class="content-sizing form-control"> &nbsp
                    <!-- <input type="submit" value="Send Button" style="width: fit-content;"> -->
                    <div class="btn btn-primary content-sizing">Send Button</div>
                </div>
            </div>
    </form>
</body>
</html>
```
``` css
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 800px;
    margin: 0 auto;
    padding-top: 50px;
}

.column {
    display: flex;
    flex-direction: column;
}
.column input {
    margin: 5px 0;
}

.content-sizing{
    height: fit-content; width: fit-content;
}
```
```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('index.html')

if __name__ == '__main__':
    app.run(debug=True)
```

