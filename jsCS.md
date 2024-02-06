## jsdatatable
code redeclare datatable biar nggk conflict waktu refresh data
```
            $.post(url, data_form,function(data) {
              data = JSON.parse(data)
                    if ($.fn.DataTable.isDataTable('#table-skrining')) {
                        // #table-skrining is a DataTable, so destroy it
                        $('#table-skrining').DataTable().destroy();
                        $('#table-skrining tbody').html(''); // Optional: Remove the table content if needed
                    }
                    // fetch data from response
                    data.forEach(ele => {
                      $('#table-skrining tbody').append(`
                      <tr class="laporanoperasi">
                        <td>${ele.tanggal}</td>
                        <td>${ele.no_rkm_medis}</td>
                        <td>${ele.nm_pasien}</td>
                        <td>${ele.diagnosa}</td>
                        <td>
                          <button class="btn btn-success btn-xs detail_skrining" data-tanggal="${ele.tanggal}" data-nr="${ele.no_rawat}">Detail</button>
                          <button class="btn btn-info btn-xs edit_skrining" data-tanggal="${ele.tanggal}" data-nr="${ele.no_rawat}">Edit</button>
                          <button class="btn btn-danger btn-xs hapus_skrining" data-tanggal="${ele.tanggal}" data-nr="${ele.no_rawat}">Hapus</button>
                        </td>
                      </tr>
                      `)
                    });
                    
                    // redeclere datatable
                    $('#table-skrining').DataTable({
                      // "order": [[ 0, "desc" ]],
                      "pagingType": "full",
                      "language": {
                        "paginate": {
                          "first": "&laquo;",
                          "last": "&raquo;",
                          "previous": "‹",
                          "next":     "›"
                        },
                        "search": "",
                        "searchPlaceholder": "Search..."
                      },
                      "lengthChange": false,
                      // "scrollX": true,
                      dom: "<<'data-table-title'><'datatable-search'f>><'row'<'col-sm-12'tr>><<'pmd-datatable-pagination' l i p>>"
                    });
            })
```

## datetimenow
function date time now

```
    function getCurrentDateTimeFormatted() {
      const now = new Date();

      // Get date components
      const year = now.getFullYear();
      const month = String(now.getMonth() + 1).padStart(2, '0');
      const day = String(now.getDate()).padStart(2, '0');

      // Get time components
      const hours = String(now.getHours()).padStart(2, '0');
      const minutes = String(now.getMinutes()).padStart(2, '0');
      const seconds = String(now.getSeconds()).padStart(2, '0');

      // Format: Y-m-d H:i:s
      const formattedDateTime = `${year}-${month}-${day} ${hours}:${minutes}:${seconds}`;

      return formattedDateTime;
    }
```

## bootbox
contoh fungsi alert bootbox
```
bootbox.confirm({
        message:"Apakah Anda Ingin Menghapus Data",
        buttons: {
              confirm: {
              label: 'Ya',
              className: 'btn-primary'
              },
              cancel: {
              label: 'Tidak',
              className: 'btn-default'
              }
              },
        callback:function(result){
          // ketika ditekan tombol ya
          if (result){
            
          }
          // ketika ditekan tombol tidak
            else{

            }
        }
      });
```

## buat_html_otomatis_dari_fetch_db
buat elemen otomatis dari fetch struktur database 

```
$(document).ready(function () {

        var baseURL = mlite.url + '/' + mlite.admin;
        event.preventDefault();

        var url = baseURL + '/rawat_inap/tablecolumn?t=' + mlite.token;
        $.post(url, {
            table: 'penilaian_medis_ranap',
        }, function (data) {
            // $('#dynamicForm').html("")
            let dataset = JSON.parse(JSON.parse(data))
            // console.log(dataset);
            // console.log(JSON.parse(data));
            $.each(dataset, function (index, field) {
                $('#dynamicForm').append(generateFormField(field));
            });
            // Add submit button
            $('#dynamicForm').append('<button type="submit" class="btn btn-primary">Submit</button>');
        });


        function generateFormField(field) {
            var $formGroup = $('<div class="form-group"></div>');

            if (field.type === 'varchar') {
                $formGroup.append('<label for="' + field.name + '">' + field.label + '</label>').append('<input type="text" class="form-control" id="' + field.name + '" name="' + field.name + '" ' + (field.maxlength ? 'maxlength="' + field.maxlength + '"' : '') + '>');
            } else if (field.type === 'datetime') {
                $formGroup.append('<label for="' + field.name + '">' + field.label + '</label>').append('<input type="date" class="form-control" id="' + field.name + '" name="' + field.name + '">');
            } else if (field.type === 'text') {
                $formGroup.append('<label for="' + field.name + '">' + field.label + '</label>').append('<textarea class="form-control" id="' + field.name + '" name="' + field.name + '" ' + (field.maxlength ? 'maxlength="' + field.maxlength + '"' : '') + '></textarea>');
            } else if (field.type === 'enum') {
                var $select = $('<select class="form-control" id="' + field.name + '" name="' + field.name + '"></select>');
                $.each(field.options, function (i, option) {
                    $select.append('<option value="' + option + '">' + option + '</option>');
                });
                $formGroup.append('<label for="' + field.name + '">' + field.label + '</label>').append($select);
            }

            return $formGroup;
        }
    });
```
