# DatePickerType

## Usage

DatePicker was designed to replace DateType which renders three `<select>` tags (year, month, day). Instead it renders one `<input>` tag. When clicked calendar widget is shown where user can easily navigate to and select desired date.

## Configuration

{% highlight yaml %}
params:
  fields:
    publishedAt:
      label:            Publication date
      formType:         datepicker
      addFormOptions:
        prepend:        Choose date
        weekstart:      1           
        format:         yyyy-MM-dd
{% endhighlight %}

## Options

#### prepend

**type:** `string` **default:** `false`

If specified, prepends input with given string.

#### weekstart

**type:** `integer` **default:** `1`

Specifies which day should start the week in calendar widget. Allowed values:

{% highlight yaml %}
0 - Sunday
1 - Monday
2 - Tuesday
3 - Wednesday
4 - Thursday
5 - Friday
6 - Saturday
{% endhighlight %}

#### format

**type:** `string` **default:** `yyyy-MM-dd`

Specifies date format. Can be any format accepted by PHP function [date()](http://www.php.net/manual/pl/function.date.php).

#### years

**type:** `array` **default:** `range(date('Y'), date('Y') - 120)`

Specifies avaliable time range. Defaults to range from current year to 120 years ago.

## DatepickerRange

Designed to replace `DateRangeType`. Renders two `Datepicker` inputs for range starting and ending date.

## Configuration

{% highlight yaml %}
params:
  fields:
    publishedAt:
      label:            Publication date
      formType:         datepicker
      addFormOptions:
        prepend:        Choose date
        weekstart:      1           
        format:         yyyy-MM-dd
builders:
  filters:
    params:
      fields:
        publishedAt:                
          formType:       datepicker_range
          formOptions:
            format: "Y-m-d"
            years:
              .range:
                from: <?php echo date("Y"); ?>
                to: 1950
                step: 1
{% endhighlight %}

>**Important!**<br />Use **formOptions** instead of **addFormOptions** to clear options from `params.fields`. If you don't, you will get <pre>The options "prepend", "weekstart" do not exist.</pre> error.

## Options

#### format

**type:** `string`

If set overwrites `from.format` and `to.format`. See `datepicker` format option above.

#### years

**type:** `array`

If set overwrites `from.years` and `to.years`. See `datepicker` years option above.

#### from

Options for starting date `datepicker` form. See `datepicker` options above.

#### to

Options for ending date `datepicker` form. See `datepicker` options above.