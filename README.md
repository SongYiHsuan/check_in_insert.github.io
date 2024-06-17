<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link rel="canonical" href="https://www.letswrite.tw/custom-google-form/">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/skeleton/2.0.4/skeleton.min.css">
  <style>
    *, *::before, *::after {
      box-sizing: border-box;
      font-size: 16px;
    }
    html, body, .container, .row {
      margin: 0;
      padding: 0;
      width: 100%;
      height: 100%;
    }
    .container {
      max-width: 100%;
    }
    button {
      font-size: 16px;
    }
    .half {
      position: fixed;
      margin: 0;
      width: 50% !important;
      height: 100%;
    }
    .bg {
      background: url('https://fakeimg.pl/1920x1024/?text=KV') center center;
      background-size: cover;
    }
    .form {
      left: 50%;
      overflow: auto;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
    }
    h1, form {
      width: 100%;
    }
    h1 {
      padding-top: 16px;
      text-align: center;
    }
    form {
      margin-right: auto;
      margin-left: auto;
      max-width: 400px;
    }
    .input-group {
      margin-bottom: 30px;
    }
    .radio-group label {
      display: inline-block;
    }
    textarea {
      min-height: 100px;
    }
    @media screen and (max-width: 1024px) {
      .half {
        position: static;
        width: 100% !重要;
        height: auto;
      }
      .bg {
        height: 30vh;
      }
      form {
        padding-right: 12px;
        padding-left: 12px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <main class="row">
      <section class="six columns half bg"></section>
      <section class="six columns half form">
        <h1>新增員工資料</h1>
        <form id="customForm">
          <div class="input-group">
            <label for="demo_name">姓名</label>
            <input class="u-full-width" type="text" id="demo_name" name="entry.2026574604" required>
          </div>
          <div class="input-group">
            <label for="demo_id">ID</label>
            <input class="u-full-width" type="text" id="demo_id" name="entry.731516791" required>
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
          <div class="input-group">
            <label for="demo_date">入職日期</label>
            <input class="u-full-width" type="date" id="demo_date" name="entry.925520126" required>
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
        event.preventDefault();
        var form = $('#customForm')[0];
        var formData = new FormData(form);
        var formParams = new URLSearchParams();
        formData.forEach((value, key) => {
          formParams.append(key, value);
        });
        fetch('https://docs.google.com/forms/u/0/d/e/1FAIpQLSf2sLvhOJGY1DFRweilnBldzWD3Hjak-nSjI5fczvvUbUA0Tg/formResponse', {
          method: 'POST',
          body: formParams.toString(),
          headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
          },
          mode: 'no-cors'
        }).then(function() {
          alert('資料已送出！');
          form.reset();
        }).catch(function(error) {
          console.error('Error:', error);
        });
      });
    });
  </script>
</body>
</html>
