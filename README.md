# Easyform
This plugin helps you create forms in html file using JQuery and with many options.

The main purpose of this plugin is to make form creation easy and more understandable.

The only thing you need to know is using of JSON in javascript!

## How to use?

As I mentioned before using this plugin is way easier than what you think! First include JQuery like below:
```
<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
```
Then download either of easyform.js or easyform.min.js ( Which will assist you better - I suggest easyform.min.js file because it's lightweight ) and include it after the JQuery including script tag like below:
```
<script src="[Path TO FILE]/easyform.min.js"></script>
```
There you go! You just installed Easyform! Easy enough? :)


Next steps are easy to do and advance.

To make a form with this plugin just add a form tag to your html file like:
```html
<!DOCTYPE html>
  <html>
    <head>
      ...
      <title>Easyform</title>
      <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
      <script src="[PATH TO FILE]/easyform.min.js"></script>
       ...
    </head>
    <body>
      ...
      <form id="easyform"></form>
      ...
    </body>
  </html>
```
And next by selecting your form and performing easyform function on it your form will be ready to use! To do so follow next steps.

First select your form and use easyform function ( better to say method ) on it after the document is ready ( Or other things that you need ).
```javascript
$(document).ready(function() {
  ...
    $('form#easyform').easyform();
  ...
});
```
After doing so you'll see that easyform wrote a text so you know easyform is there for you. :D

Easyform as deafult uses a class called ```easyform-default``` which will be ready to use out of box which makes forms look a bit cleaner than usual, if you import css like below:
```javascript
$(document).ready(function() {
  ...
    $('head').easyformImportStyles();
    $('form#easyform').easyform();
  ...
});
```
After doing so styles will be added to head of your html document or you can add them somewhere else.

There are two arguments needed for this function. First is ```inputs``` and second ```options```. Both are using JSON so try to get familiar with it. :)

```inputs``` are taking place at the first and we will follow the steps one by one.

```inputs``` are the main parts of form and your main concern to deal with in Easyform. To make inputs of any kind you need to use JSON with some options in an array so Easyform can get your ideas and make it for you.

Sample:
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "text",
      label: "Firstname"
    }
  ];
  $('form#easyform').easyform(inputs);
});
```
Every JSON objects will make an input or button ( next we'll talk about ) with some available options which some are mandatory and some are not.
Available options for every input is like below:

Row | Name | Value(s) | Description | Default | Mandatory
--- | ---- | ------ | ----------- | ------- | ---------
1 | ```type``` | ```text```, ```password```, ```email```, ```number```, ```file```, ```textarea```, ```select```, ```radio```, ```checkbox```, ```sumbit```, ```reset```, ```button``` | This option will define which kind of input you want to be created. | ```text``` | Yes ( If not defined deafult will be replaced )
2 | ```label``` | Any string | This option will define a label. | A string like: input[Input Number]. Like input1 - input2 ... | Yes ( If not defined deafult will be replaced )
3 | ```name``` | Any string | This option defines name of input. | A string like: input[Input Number]. Like input1 - input2 ... | Yes ( If not defined deafult will be replaced )
4 | ```id``` | Any string | This option defines id of input. | A string like: input[Input Number]. Like input1 - input2 ... | Yes ( If not defined deafult will be replaced )
5 | ```attrs``` | An array with JSON objects | Using this option you can define attrs for an input | None | No
6 | ```value``` | Any string | This option defines default value for inputs which accept values | None | No
7 | ```placeholder``` | Any string | This option defines default value for inputs which accept placeholders | None | No
8 | ```options``` | An array with JSON objects | Using this option you can define options for ```select``` type inputs and boxes for ```radio``` and ```checkbox``` type inputs. | None | No ( If not defined nothing will show up :D )

These are all options for ```inputs``` and using them are easy and next I'll show you some examples.

__*Warning: None of two or more inputs can have same id, If you do so easyform will throw error but will continue with other inputs.*__

### Inputs

#### Creating two inputs for username and password.
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "text",
      label: "Username",
      placeholder: "Enter your username..."
    },
    {
      type: "password",
      label: "Password",
      placeholder: "Enter your password..."
    }
  ];
  $('form#easyform').easyform(inputs);
});
```
This code will create to inputs with labels and two kinds of input which first is ```text``` and second is ```password```.

If you want to define file type input you can use ```file``` as value of ```type``` in your object.

__*Dev note: As you know for sending files through forms, form enctype should be equal to ```multipart/form-data```. In Easyform there is no need to define this as if there is file type input in a form this will automatically be fixed. But ofcourse you can change it if you want other kinds.*__

#### Creating country selecting ```select```, ```radio```, ```checkbox```:

Doing so is very easy and so transforming them to eachother is.

To define options in select box you need to use ```options``` option in you json which will need another JSON combination included in an array.
```javascript
$(document).ready(function() {
$('head').easyformImportStyles();
var inputs = [
  {
    type: "select",
    label: "Country",
    name: "country",
    options: [
      {text: "Iran", value: "IR"},
      {text: "India", value: "IN"},
      {text: "Turkey", value: "TR"},
      {text: "Germany", value: "DE"},
      {text: "United Kingdom", value: "UK"},
      {text: "United states of America", value: "US"}
    ]
  }
];
$('form#easyform').easyform(inputs);
});
```
This code will create a select box with 6 options to choose. You can also define unique id for every option in select boxes like below:
```javascript
$(document).ready(function() {
$('head').easyformImportStyles();
var inputs = [
  {
    type: "select",
    label: "Country",
    name: "country",
    options: [
      {text: "Iran", value: "IR", id: "one"},
      {text: "India", value: "IN", id: "two"},
      {text: "Turkey", value: "TR", id: "three"},
      {text: "Germany", value: "DE", id: "four"},
      {text: "United Kingdom", value: "UK", id: "five"},
      {text: "United states of America", value: "US", id: "six"}
    ]
  }
];
$('form#easyform').easyform(inputs);
});
```
__*Warning: You can't define id for radio and checkbox options because they will be defined automatically.*__

Changing from select box to radio and checkbox is very easy that you might not believe! Just change the type from ```select``` to either of ```radio``` or ```checkbox```, and... hmmmm that's it :D.
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "radio",
      label: "Country",
      name: "country",
      options: [
        {text: "Iran", value: "IR"},
        {text: "India", value: "IN"},
        {text: "Turkey", value: "TR"},
        {text: "Germany", value: "DE"},
        {text: "United Kingdom", value: "UK"},
        {text: "United states of America", value: "US"}
      ]
    }
  ];
  $('form#easyform').easyform(inputs);
});
```
Or
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "checkbox",
      label: "Country",
      name: "country",
      options: [
        {text: "Iran", value: "IR"},
        {text: "India", value: "IN"},
        {text: "Turkey", value: "TR"},
        {text: "Germany", value: "DE"},
        {text: "United Kingdom", value: "UK"},
        {text: "United states of America", value: "US"}
      ]
    }
  ];
  $('form#easyform').easyform(inputs);
});
```
Both of codes will create radio or checkbox inputs with same options.

__*Dev note: If you choose checkbox type at the end of every checkbox's name there will be additional ```[]``` which is used to get multiple checkbox values in PHP.*__

### Buttons
Defining buttons are as easy as inputs were. The only thing you need is change the type to either of ```submit```, ```reset``` or ```button```. And using ```text``` option will define text that is shown in button.
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "submit",
      text: "Gon on!"
    }
  ];
  $('form#easyform').easyform(inputs);
});
```
The upper code will create a submit button which will show ```Go on!``` text inside it.

## Advanced

### Attributes
As you've seen in the options table you can use ```attrs``` option to define attributes for elements like below:
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "number",
      label: "My number",
      attrs: [
        {name: "min", value: "50"},
        {name: "max", value: "70"}
      ]
    }
  ];
  $('form#easyform').easyform(inputs);
});
```
This code will create an input of ```number``` type which have min and max attributes of 50 and 70. You can also define classes like this. If you want multiple classes just use space between them.
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "number",
      label: "My number",
      attrs: [
        {name: "min", value: "50"},
        {name: "max", value: "70"},
        {name: "class", value: "a b c"}
      ]
    }
  ];
  $('form#easyform').easyform(inputs);
});
```

## Form Options
In case you need to deal with form tag itself you can pass another JSON object as the second argument in the easyform function.

Available options for this argoument is listed below:

Row | Name | Value(s) | Description | Default | Mandatory
--- | ---- | ------ | ----------- | ------- | ---------
1 | ```styleClass``` | Any String | This option defines class or classes used for form. | ```easyform-default``` | No
2 | ```action``` | Any string | This option defines action attribute of form element. | None | No
3 | ```method``` | Any string | This option defines method attribute of form element. | None | No
4 | ```enctype``` | Any string | This option defines enctype attribute of form element. | None | No
5 | ```attrs``` | An array with JSON objects | Using this option you can define other attributes for the form. | None | No

A complete sample:
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "file",
      name: "myfile"
    }
  ];
  var formOptions = {
    styleClass: "a",
    action: "handle.php",
    method: "POST",
    attrs: [
      {name: "data-test", value: "44"},
      {name: "data-hello", value: "55"}
    ]
  };
  $('form#easyform').easyformDebug();
  $('form#easyform').easyform(inputs, formOptions);
});
```
In this code we defined class, action, method and some other attributes for the form we're working on.

__*Dev note: As mentioned before if there is file type input the enctype attribute of the form will automatically be set as ```multipart/form-data``` but if you want to change it you can define it with ```enctype``` option which is first priority and can't be changed if there is file type input.*__

Example:
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "file",
      name: "myfile"
    }
  ];
  var formOptions = {
    styleClass: "a",
    action: "handle.php",
    method: "POST",
    enctype: "anything",
    attrs: [
      {name: "data-test", value: "44"},
      {name: "data-hello", value: "55"}
    ]
  };
  $('form#easyform').easyformDebug();
  $('form#easyform').easyform(inputs, formOptions);
});
```

## Debug Mode
This option will make debug mode on for each form selected and you can see errors for every input you defined and also complete description in log console.
To turn this mode on use ```easyformDebug``` function just before you call ```easyform``` function like below:
```javascript
$(document).ready(function() {
  $('head').easyformImportStyles();
  var inputs = [
    {
      type: "aaa"
    },
    {
      type: "text",
      id: "hello"
    },
    {
      type: "text",
      id: "hello"
    }
  ];
  $('form#easyform').easyformDebug();
  $('form#easyform').easyform(inputs);
});
```
This code will turn debug mode on and will generate two errors.

First error is because of first input type which is 'aaa' and not defined in Easyform.

Second error is because of id of second and third inputs which are same.

Instead of skipping errors it will show that there was a problem with it and for more details you can open your browsers log console and see what's going on.
