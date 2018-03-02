# Easyform
This plugin helps you create forms in html file using JQuery and with many options.

The main purpose of this plugin is to make form creation easy and more understandable.

The only thing you need to know is using of JSON in javascript!

##How to use?

As I mentioned before using this plugin is way easier than what you think! just include JQuery like below:
```
<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
```
Then download either of easyform.js or easyform.min.js ( Which will assist you better - I suggest easyform.min.js file because it's lightweight ) and include in after the JQuery including script tag like below:
```
<script src="[Path TO FILE]/easyform.min.js"></script>
```
There you go! You just installed Easyform! Easy enough? :)


Next steps are easy to do and advance.

To make a form with this plugin just add a form tag to your html file like:
```
<!DOCTYPE html>
  <html>
    <head>
      ...
      <title>Easyform</title>
      <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
      <script src="[Path TO FILE]/easyform.min.js"></script>
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
```
<script>
  $(document).ready(function() {
    ...
      $('form#easyform').easyform();
    ...
  });
</script>
```
After doing so you'll see that easyform wrote a text so you know easyform is there for you. :D

There are two arguments needed for this function. First is ```inputs``` and second ```options```. Both are using JSON so try to get familiar with it. :)

```inputs``` are taking place at the first and we will follow the steps one by one.

```inputs``` are the main parts of form and your main concern to deal with in Easyform. for making inputs of anykind you need to use JSON with some options in an array so easyform can get your ideas and make it for you.

Sample:
```
$(document).ready(function() {
  var inputs = [
    {
      type: "text",
      label: "Firstname"
    }
  ];
  $('form#easyform').easyform(inputs);
});
```
Every json combination of JSON objects will make an input or button ( next we'll talk about ) with some available options which some are mandatory and some are not.
Available options for every input is like below:

Row | Name | Values | Description | Default | Mandatory
--- | ---- | ------ | ----------- | ------- | ---------
1 | ```type``` | ```text```, ```password```, ```email```, ```number```, ```textarea```, ```select```, ```radio```, ```checkbox```, ```sumbit```, ```reset```, ```button``` | This option will define which kind of input you want to be created. | ```text``` | Yes ( If not defined deafult will be replaced )
2 | ```label``` | Any string | This option will define a label. | A string like: input[Row Number]. Like input1 - input2 ... | Yes ( If not defined deafult will be replaced )
3 | ```name``` | Any string | This option defines name of input. | A string like: input[Row Number]. Like input1 - input2 ... | Yes ( If not defined deafult will be replaced )
4 | ```id``` | Any string | This option defines id of input. | A string like: input[Row Number]. Like input1 - input2 ... | Yes ( If not defined deafult will be replaced )
5 | ```attrs``` | An array with JSON objects | Using this option you can define attrs for an input | None | No
6 | ```value``` | Any string | This option defines default value for inputs which accept values | None | No
7 | ```placeholder``` | Any string | This option defines default value for inputs which accept placeholders | None | No
8 | ```options``` | An array with JSON objects | Using this option you can define options for ```select``` type inputs and boxes for ```radio``` and ```checkbox``` type inputs. | None | No ( If not defined nothing will show up :D )

These are all options for ```inputs``` and using them are easy and next I'll show you some examples.
