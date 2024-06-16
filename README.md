<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  
  <link rel="canonical" href="https://www.letswrite.tw/custom-google-form/">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/skeleton/2.0.4/skeleton.min.css">

  <style>
    /* Styles here */
  </style>

  <link rel="shortcut icon" href="https://letswritetw.github.io/letswritetw/dist/img/logo_512.png"/>
  <script>
    (function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
    new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
    j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
    'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
    })(window,document,'script','dataLayer','GTM-PGQ9WQT');
  </script>
</head>
<body>
  <noscript>
    <iframe src="https://www.googletagmanager.com/ns.html?id=GTM-PGQ9WQT" height="0" width="0" style="display:none;visibility:hidden"></iframe>
  </noscript>

  <div class="container">
    <main class="row">
      <section class="six columns half bg"></section>
      <section class="six columns half form">
        <h1>Contact us</h1>
        <form id="customForm">
          <div class="input-group">
            <label for="demo_name">姓名</label>
            <input class="u-full-width" type="text" id="demo_name" name="entry.2026574604">
          </div>
          <div class="input-group">
            <label for="demo_id">ID</label>
            <input class="u-full-width" type="text" id="demo_id" name="entry.731516791">
          </div>
          <div class="input-group">
            <label>性別</label>
            <div class="radio-group row">
              <div class="four columns">
                <input type="radio" id="male" name="entry.959970287" value="male" checked>
                <label for="male">男性</label>
              </div>
              <div class="four columns">
                <input type="radio" id="female" name="entry.959970287" value="female">
                <label for="female">女性</label>
              </div>
            </div>
          </div>
          <button type="button" id="submit" class="button-primary u-full-width">確認送出</button>
        </form>
      </section>
    </main>
  </div>

  <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
  <script>
    $(function() {
      $('#submit').on('click', function(event) {
        event.preventDefault(); // Prevent default form submission

        var form = $('#customForm')[0];
        var formData = new FormData(form);

        fetch('https://docs.google.com/forms/u/0/d/e/1FAIpQLSf2sLvhOJGY1DFRweilnBldzWD3Hjak-nSjI5fczvvUbUA0Tg/formResponse', {
          method: 'POST',
          body: formData,
          mode: 'no-cors'
        }).then(function() {
          alert('資料已送出！');
          form.reset(); // Reset form
        }).catch(function(error) {
          console.error('Error:', error);
        });
      });
    });
  </script>
</body>
</html>
