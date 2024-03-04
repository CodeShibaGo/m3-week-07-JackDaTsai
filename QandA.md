## 什麼是 CSRF Token 與如何使用

### 什麼是 CSRF 攻擊

CSRF 是指跨站的請求偽造，這種攻擊方法會強迫使用者在他們已經驗證身份的網站中，執行某些惡意的偽造操作，因為已經驗證過該使用者，所以網站就會以操作來自該使用者，因此接受了該操作。舉例來說，某個使用者登入銀行帳戶後，去逛別的網站，但不小心點開惡意網站，該惡意網站中的程式碼用這名使用者的名義，進行未經同意的轉帳操作。

CSRF 之所以成立，是因為使用者的身份已經先被驗證過。如果要白話一點理解，就像是別人偷拿你的會員點數卡去買東西。但因為店家認卡，所以當看到小偷拿著你的卡，就相信小偷是你本人，於是接受該小偷使用你的點數進行消費。

### 實作

```bash
pip install flask### wtf
```

```python
import os
from flask_wtf.csrf import CSRFProtect
 
app.config['SECRET_KEY'] = os.urandom(24)
 
csrf = CSRFProtect(app)
```

```html
<form method="post">
    <input type="hidden" name="csrf_token" value="{{ csrf_token() }}"/>
    <input type="text" name="email" class="form-control form-control-lg" placeholder="max@email.com">
</form>
```

```javascript
var csrf = "{{ csrf_token() }}";
axios.post('/auth/login', data, {
        headers: {'x-csrf-token': csrf}
        })
```

## 學會 VS Code + VirtualEnv 組合技巧

```bash
python -m venv .venv
```

```bash
source .venv/bin/activate
```

