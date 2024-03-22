jquery each for collect data from form_data

```
let data_form = {}
$('.data-exam').each(function () {
  const id = $(this).attr('id');
  if (!data_form.hasOwnProperty(id)) {
    data_form[id] = $(this).val();
  }
});
```

jquery checkbox clicked validation

```
  if ($("#myCheckbox").is(":checked")) {
      console.log("Checkbox is checked");
  } else {
      console.log("Checkbox is not checked");
  }
```

jquery hidden prop

```
  if ($("#myElement").is(':hidden')) {
      $("#myElement").prop('hidden', false);
  } else {
      $("#myElement").prop('hidden', true);
  }
```
