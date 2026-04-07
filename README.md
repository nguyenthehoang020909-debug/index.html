<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MB Bank Pro</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root { --mb-blue: #003399; --mb-gold: #f0c419; }
        body { font-family: 'Arial', sans-serif; margin: 0; background: #f4f7fa; user-select: none; -webkit-tap-highlight-color: transparent; }
        .page { display: none; height: 100vh; width: 100vw; position: absolute; overflow-y: auto; }
        .active { display: block; }
        
        /* Login */
        #login-page { background: linear-gradient(135deg, #001a4d 0%, #003399 100%); color: white; text-align: center; display: flex; flex-direction: column; justify-content: center; }
        .login-box { background: rgba(255,255,255,0.1); width: 85%; margin: 0 auto; padding: 30px 20px; border-radius: 20px; backdrop-filter: blur(10px); }
        
        /* Home */
        .header-home { background: var(--mb-blue); color: white; padding: 40px 20px 60px; border-radius: 0 0 30px 30px; position: relative; }
        .card-balance { background: white; width: 90%; margin: -40px auto 20px; border-radius: 20px; padding: 20px; box-shadow: 0 8px 20px rgba(0,0,0,0.1); box-sizing: border-box; }
        .menu-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 15px; padding: 10px 20px; text-align: center; }
        .menu-item i { width: 50px; height: 50px; background: white; border-radius: 15px; display: flex; align-items: center; justify-content: center; margin: 0 auto 8px; color: var(--mb-blue); box-shadow: 0 4px 10px rgba(0,0,0,0.05); font-size: 20px; }
        .menu-item p { font-size: 11px; font-weight: 500; color: #333; margin: 0; }

        /* Input */
        .app-bar { background: white; padding: 15px; display: flex; align-items: center; border-bottom: 1px solid #eee; color: var(--mb-blue); font-weight: bold; }
        .form-group { padding: 20px; }
        label { font-size: 13px; color: #666; font-weight: bold; }
        input { width: 100%; padding: 15px; margin: 8px 0 20px; border: 1px solid #ddd; border-radius: 12px; box-sizing: border-box; font-size: 16px; }
        .btn-main { background: var(--mb-blue); color: white; border: none; width: 90%; padding: 16px; border-radius: 30px; font-weight: bold; font-size: 16px; margin: 20px auto; display: block; }
    </style>
</head>
<body>

    <div id="login-page" class="page active">
        <h1 onclick="buffMoney()" style="letter-spacing: 3px;">MB <span style="font-weight: 100; color: var(--mb-gold);">PRIORITY</span></h1>
        <div class="login-box">
            <p style="opacity: 0.8;">Xin chào,</p>
            <h2 style="margin: 5px 0 25px;">NGUYỄN THẾ HOÀNG</h2>
            <input type="password" placeholder="Mật khẩu" style="background: rgba(255,255,255,0.15); border: none; color: white; text-align: center;">
            <button class="btn-main" style="background: #71c9f8; color: var(--mb-blue); width: 100%;" onclick="showPage('home-page')">VÂN TAY / FACEID</button>
        </div>
    </div>

    <div id="home-page" class="page">
        <div class="header-home">
            <div style="display: flex; justify-content: space-between; align-items: center;">
                <span style="font-weight: bold; font-size: 20px;">MB</span>
                <div style="display: flex; gap: 15px;"><i class="fa-solid fa-magnifying-glass"></i><i class="fa-solid fa-bell"></i></div>
            </div>
            <p style="font-size: 13px; opacity: 0.8; margin-top: 15px;">Chúc bạn một ngày tốt lành!</p>
        </div>
        <div class="card-balance">
            <p style="color: #888; font-size: 12px; margin-bottom: 5px;">VND - Tài khoản nguồn <i class="fa-solid fa-chevron-right" style="font-size: 8px;"></i></p>
            <h2 id="main-balance" style="color: var(--mb-blue); margin: 0;">87,888,736 VND</h2>
        </div>
        <div class="menu-grid">
            <div class="menu-item" onclick="showPage('transfer-page')"><i class="fa-solid fa-paper-plane"></i><p>Chuyển tiền</p></div>
            <div class="menu-item"><i class="fa-solid fa-qrcode"></i><p>Quét QR</p></div>
            <div class="menu-item"><i class="fa-solid fa-wallet"></i><p>Tiền gửi</p></div>
            <div class="menu-item"><i class="fa-solid fa-shield-halved"></i><p>Bảo hiểm</p></div>
        </div>
    </div>

    <div id="transfer-page" class="page">
        <div class="app-bar">
            <i class="fa-solid fa-chevron-left" onclick="showPage('home-page')"></i>
            <span style="margin-left: 20px;">Chuyển tiền tới số tài khoản</span>
        </div>
        <div class="form-group">
            <label>SỐ TÀI KHOẢN NHẬN</label>
            <input type="number" id="stk" placeholder="Nhập STK người nhận">
            <labe
