file cheatsheet haekal

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
