jquery each for collect data from form_data

let data_form = []
$('.className').each(function () {
  data_form[$(this).attr('id')] = $(this).val()
})
