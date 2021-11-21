---
name: "Laravel WordPress Development"
ordem: 3
rg: "orgem-geral-ptbr-v1"
idioma: "PT-BR"
intenção: "Informações sobre o front-end."
sumário Prático: "Use o front-end."
descrição Mozilla: "Front-end é."
descrição WP: "Front-end é."
descrição W3C: "Front-end é."
descrição Google: "Front-end é."
tempo Estimado: "(1 hora, 30 minutos, 5 horas)" <!-- // (min, tool, hard) -
---

# Laravel WordPress Development

# Views

# App

Controllers

Options

admin

filters

helpers

setup

Logics here

Ajax

```php
namespace App;

$something = (function({
  // do something cool
}))

add_action($hook_name, $something, $priority = 10, $accepted_args = 1 );


/**
 * Theme assets
 */

add_action('wp_enqueue_scripts', function () {
    wp_enqueue_script('ajax-login.js', asset_path('scripts/ajax-login.js'), ['jquery'], null, true);
}, 100);
```

```js
jQuery(document).ready(function () {
  var Success = false;
  var ajaxscript = { ajax_url: "http://localhost/wp-admin/admin-ajax.php" };
  jQuery("#wp-submit").on("click", function (e) {
    e.preventDefault();
    var data = {
      action: "login_init",
      user: jQuery("#email-input").val(),
      pwd: jQuery("#password-input").val(),
    };
    jQuery.ajax({
      url: ajaxscript.ajax_url,
      xhrFields: {
        withCredentials: true,
      },
      type: "POST",
      data: data,
      beforeSend: function () {
        console.log("post--->send");
      },
      success: function (response) {
        console.log("sucess: ");
        console.log(response);
        console.log(data);
        Success = true;
        document.location.href = "http://localhost/zumba";
      },
      error: function (response) {
        console.log("error: ");
        console.log(response);
        Success = false;
      },
    });
    return Success;
  });
});
```

Config

Resources

Dist, Node Modules and Vendor
