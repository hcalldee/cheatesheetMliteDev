## Snippets

Snippets VS Code <br>
instalasi File > Preferences > Configure User Snippets
copas code dibawah

    // in file 'Code/User/snippets/javascript.json'
    {
      "Buat Jquery Click": {
        "prefix": ["jquery-click", "JC"],
        "body": ["$('#').click(function () {})"],
        "description": "buat struktur on click function jquery"
      }
    }

1. prefix untuk trigger
2. body adalah kode yang ingin dihasilkan
3. description untuk dokumentasi
<br><br>

```
    // in file 'Code/User/snippets/javascript.json'
{
	"For Loop": {
	  "prefix": ["jquery-click", "JC"],
	  "body": ["$('#').click(function () {})"],
	  "description": "buat fungsi jquery."
	},
	"this val": {
		"prefix": ["thisval", "TV"],
		"body": ["$(this).val()"],
		"description": "buat this val."
	  },
	"val": {
		"prefix": ["val", "TV"],
		"body": ["$('#').val()"],
		"description": "buat this val."
	},
	"this sel val": {
	"prefix": ["thisselval", "TSV"],
	"body": ["$(this).find('option:selected').val()"],
	"description": "buat this val."
	},
	"this attr": {
		"prefix": ["thisattr", "TA"],
		"body": ["$(this).attr('')"],
		"description": "buat this attr."
	  },
	"jquery each": {
		"prefix": ["jquery-each", "JE"],
		"body": ["$('').each(function () {\n\n})"],
		"description": "buat this attr."
	},
	"jquery post": {
		"prefix": ["jquery-post", "JP"],
		"body": ["let baseURL = mlite.url + '/' + mlite.admin;\nlet url    = baseURL + '/rawat_inap/simpanskrining?t=' + mlite.token;\n$.post(url, data_form,function(data) {\n\n\n});"],
		"description": "buat this attr."
	},
	"php dump": {
		"prefix": ["debug", "VD"],
		"body": ["{? $$this->core->debug($) ?}"],
		"description": "debug di view"
	},
  }
```
