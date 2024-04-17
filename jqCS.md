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


selectator redefining collection
```
 $('#kd_pj').change(function () {
      let baseURL = mlite.url + '/' + mlite.admin;
      let url    = baseURL + '/dokter_ralan/ambilPaketOperasi?t=' + mlite.token;
      let data_form = {
        kd_pj:$(this).val()
      }
      $.post(url, data_form,function(data) {
        data = JSON.parse(data)
        $("#kode_paket").selectator('destroy');
        $("#kode_paket").empty();
        data.forEach(ele => {
          $("#kode_paket").append($('<option>').val(ele.kode_paket).text(`${ele.nm_perawatan} - (${ele.kode_paket})`));
        });
        $("#kode_paket").selectator();
      });
    })
```
