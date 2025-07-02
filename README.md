# kvartira.kg

<!DOCTYPE html>
<html lang="ky">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Квартира Издөө Сайты</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: linear-gradient(135deg, #f4e4Bc, #e8c07d, #d4a373, #a67b5b);
            background-size: 400% 400%;
            animation: gradientBG 12s ease infinite;
            color: #333;
            overflow-x: hidden;
            line-height: 1.6;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .header {
            background-color: rgba(255, 98, 0, 0.95);
            color: white;
            text-align: center;
            padding: 30px 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            position: relative;
            z-index: 10;
        }

        .header h1 {
            font-size: 2.5rem;
            letter-spacing: 1px;
            text-transform: uppercase;
            animation: fadeInDown 1s ease-out;
        }

        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .warning {
            background-color: rgba(255, 255, 0, 0.95);
            color: #333;
            text-align: center;
            padding: 15px;
            margin: 20px auto;
            max-width: 800px;
            border-radius: 8px;
            font-size: 1.1rem;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            animation: fadeIn 1s ease-out;
        }

        .warning button {
            background-color: #ff6200;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s, transform 0.2s;
        }

        .warning button:hover {
            background-color: #e65c00;
            transform: translateY(-2px);
        }

        .container {
            max-width: 1400px;
            margin: 30px auto;
            padding: 0 20px;
        }

        .listing {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .card {
            background: rgba(255, 255, 255, 0.98);
            border: 1px solid #ddd;
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
            transition: transform 0.3s, box-shadow 0.3s;
            animation: fadeInUp 0.5s ease-out;
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .card img {
            width: 100%;
            height: 220px;
            object-fit: cover;
            border-radius: 8px;
            transition: transform 0.3s;
        }

        .card img:hover {
            transform: scale(1.03);
        }

        .card .price {
            color: #27ae60;
            font-weight: bold;
            font-size: 1.3rem;
            margin: 10px 0;
            text-align: center;
        }

        .card h3 {
            font-size: 1.2rem;
            color: #2c3e50;
            margin: 10px 0;
        }

        .card p {
            color: #7f8c8d;
            font-size: 0.95rem;
            margin: 5px 0;
        }

        .btn-group {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-top: 15px;
            flex-wrap: wrap;
        }

        .contact-btn {
            display: inline-block;
            padding: 12px 25px;
            background-color: #ff6200;
            color: white;
            text-decoration: none;
            border-radius: 6px;
            font-size: 0.9rem;
            font-weight: 500;
            transition: background-color 0.3s, transform 0.2s, box-shadow 0.3s;
        }

        .contact-btn:hover {
            background-color: #e65c00;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .language-switch {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
            display: flex;
            gap: 10px;
        }

        .language-switch button {
            padding: 8px 15px;
            background-color: #ff6200;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: background-color 0.3s, transform 0.2s;
        }

        .language-switch button:hover {
            background-color: #e65c00;
            transform: translateY(-2px);
        }

        .admin-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            padding: 12px 25px;
            background-color: #2ecc71;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 500;
            transition: background-color 0.3s, transform 0.2s;
        }

        .admin-btn:hover {
            background-color: #27ae60;
            transform: translateY(-2px);
        }

        #agreement {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(255, 255, 255, 0.98);
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
            text-align: center;
            z-index: 2000;
            max-width: 500px;
            animation: fadeIn 0.5s ease-out;
        }

        #agreement p {
            font-size: 1.1rem;
            color: #333;
            margin-bottom: 15px;
        }

        #agreement button {
            padding: 12px 25px;
            background-color: #ff6200;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s, transform 0.2s;
        }

        #agreement button:hover {
            background-color: #e65c00;
            transform: translateY(-2px);
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 1024px) {
            .listing {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 768px) {
            .listing {
                grid-template-columns: 1fr;
            }

            .header h1 {
                font-size: 1.8rem;
            }

            .warning {
                font-size: 1rem;
                padding: 10px;
            }

            .card {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div id="agreement">
        <p>Саламатсызбы, колдонуучу! Сиздин коопсуздугуңуз үчүн эскертебиз: Квартира боюнча онлайн сүйлөшүүдө акча которбоңуз. Квартираны өзүңүз көрүп, толук маалымат алгандан кийин гана, ишенимдүү болсо, келишим түзүңүз.</p>
        <p>Здравствуйте, пользователь! Для вашей безопасности предупреждаем: Не переводите деньги онлайн при обсуждении квартиры. Осмотрите квартиру лично и получите полную информацию, заключайте сделку только при полной уверенности.</p>
        <button onclick="document.getElementById('agreement').style.display='none'; document.body.style.overflow='auto';">Макул / Согласен</button>
    </div>
    <div class="language-switch">
        <button onclick="changeLanguage('ky')">Кыргызча</button>
        <button onclick="changeLanguage('ru')">Русский</button>
    </div>
    <div class="header">
        <h1>Квартира Издөө Сайты</h1>
    </div>
    <div class="warning" id="warningMessage">
        <p>Саламатсызбы, колдонуучу! Сиздин коопсуздугуңуз үчүн эскертебиз: Квартира боюнча онлайн сүйлөшүүдө акча которбоңуз. Квартираны өзүңүз көрүп, толук маалымат алгандан кийин гана, ишенимдүү болсо, келишим түзүңүз.</p>
        <p>Здравствуйте, пользователь! Для вашей безопасности предупреждаем: Не переводите деньги онлайн при обсуждении квартиры. Осмотрите квартиру лично и получите полную информацию, заключайте сделку только при полной уверенности.</p>
        <button onclick="document.getElementById('warningMessage').style.display='none'; document.getElementById('agreement').style.display='block'; document.body.style.overflow='hidden';">Макул / Согласен</button>
    </div>
    <div class="container">
        <div class="listing">
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">Сүйлөшүлөт / По договоренности</div>
                <h3>Кв Берилет АК оргодон / Квартира в Ак-Ордо</h3>
                <p>Адрес: АК Ордо</p>
                <div class="btn-group">
                    <a href="tel:+996502005197" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996502005197" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">7 500 сом / 7500 сом</div>
                <h3>КВАРТИРА - ПОДСИЛЕНИЕМ / Квартира с подселением</h3>
                <p>Срочно, 1 бала керек, таза жашаган</p>
                <p>Ремонт жакшы, бардык техникалар, Аристон бар</p>
                <p>Адрес: Исы Ахунбаева 139а, Ата-Турк, Политех</p>
                <div class="btn-group">
                    <a href="tel:+996501988966" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996501988966" class="contact-btn">WhatsApp</a>
                    <a href="tel:+996502018401" class="contact-btn">Звонок 2</a>
                    <a href="https://wa.me/+996502018401" class="contact-btn">WhatsApp 2</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">Сүйлөшүлөт / По договоренности</div>
                <h3>Срочно сдаю комнату с подселением / Комната берилет</h3>
                <p>5 мкр, бардык шарттар, фото ватсапта</p>
                <div class="btn-group">
                    <a href="tel:+996555223367" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996555223367" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">20 000 сом, депозит 5 000 сом</div>
                <h3>Комната берилет / Сдается комната</h3>
                <p>Бардык коммуникациялар, Ахунбаева/Малдыбаева</p>
                <p>Район: Политех, Мед академия, КГУСТА</p>
                <div class="btn-group">
                    <a href="tel:+996555885561" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996555885561" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">Сүйлөшүлөт / По договоренности</div>
                <h3>Чогу жашаганга 1 кыз керек / Нужна 1 девушка для совместного проживания</h3>
                <p>Срочно, элитный квартира, таза жашаган</p>
                <p>Адрес: Малая Гвардия</p>
                <div class="btn-group">
                    <a href="tel:+996705787817" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996705787817" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">20 000 сом, депозит 5 000 сом</div>
                <h3>Общагадан бир чон комната берилет / Сдается большая комната в общежитии</h3>
                <p>Кухня, душ, туалет 5 бөлмөгө орток</p>
                <p>Политех, Мед академия, КГУСТА</p>
                <div class="btn-group">
                    <a href="tel:+996555885561" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996555885561" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">11 000 сом</div>
                <h3>Комната берилет / Сдается комната</h3>
                <p>Азия Молл, ТЦга жакын, бардык шарттар</p>
                <div class="btn-group">
                    <a href="tel:+996550025039" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996550025039" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">5 000 сом киши башына / 5000 сом с человека</div>
                <h3>1 комнатный квартирага 2 бала керек / Нужны 2 человека в 1-комнатную квартиру</h3>
                <p>Ичпеген, чекпеген, Дордой Кербен стоянкага жакын</p>
                <p>Бардык шарттар бар</p>
                <div class="btn-group">
                    <a href="tel:+996550017157" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996550017157" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">20 000 сом</div>
                <h3>Сдается комната с подселением / Комната берилет</h3>
                <p>3-х комнатная квартира</p>
                <p>Для 2 девушек, со всеми условиями</p>
                <p>Район: Восток-5</p>
                <div class="btn-group">
                    <a href="tel:+996550176716" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996550176716" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">42 000 сом/месяц</div>
                <h3>Сдается 3-х комнатная квартира / 3 бөлмөлүү квартира берилет</h3>
                <p>Со всеми условиями / Бардык шарттар менен</p>
                <p>Адрес: ул. Киевская/М. Гвардия</p>
                <div class="btn-group">
                    <a href="tel:+996707200519" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996707200519" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Студия-квартира">
                <div class="price">15 000 сом, депозит 3 000 сом</div>
                <h3>КВАРТИРА БЕРИЛЕТ / Сдается квартира</h3>
                <p>Студия-квартира</p>
                <p>Район: Западный Автовокзал - Ош базар</p>
                <div class="btn-group">
                    <a href="tel:+996508881486" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996508881486" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="1-комнатная квартира">
                <div class="price">8 000 сом + 5 000 депозит</div>
                <h3>КВАРТИРА БЕРИЛЕТ / Сдается квартира</h3>
                <p>Ак-Өргө, ул. Ахунбаева Кырк-Кыз</p>
                <p>1 бөлмөлүү, душ жок, 2 адамга ылайыктуу</p>
                <div class="btn-group">
                    <a href="tel:+996705406590" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996705406590" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="1-комнатная квартира">
                <div class="price">9 000 сом</div>
                <h3>Квартира берилет, без хозяин / Сдается квартира без хозяина</h3>
                <p>Район: Стеклозавод, дордойго жакын</p>
                <p>Времянка, 1 комната, суу, туалет эшикте, огороженный</p>
                <div class="btn-group">
                    <a href="tel:+996224281431" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996224281431" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="1-комнатная квартира">
                <div class="price">15 000 сом</div>
                <h3>Сдается 1 ком кв / 1 бөлмөлүү квартира берилет</h3>
                <p>Район: Кызыл Аскер, душ туалет бар</p>
                <div class="btn-group">
                    <a href="tel:+996508303975" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996508303975" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">20 000 сом</div>
                <h3>Сдается квартира гостининого типа / Гостини типтеги квартира берилет</h3>
                <p>Ж/м Ак-Ордо, ул. Сыпайы 5, со всеми условиями</p>
                <p>Коммуналдык төлөмдөр кирет</p>
                <div class="btn-group">
                    <a href="tel:+996706811007" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996706811007" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">30 000 сом, депозит 10 000 сом</div>
                <h3>КВАРТИРА / Квартира берилет</h3>
                <p>Ак Оргодон, жаны батир</p>
                <div class="btn-group">
                    <a href="tel:+996502625212" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996502625212" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">28 000 сом, депозит 5 000 сом</div>
                <h3>Сдаю квартиру в 4 мкр / 4 мкрдан квартира берилет</h3>
                <p>Только семейным, ортосайга жакын</p>
                <div class="btn-group">
                    <a href="tel:+996505919919" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996505919919" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">35 000 сом + 15 000 депозит</div>
                <h3>Сдаю 1 комнатную квартиру / 1 бөлмөлүү квартира берилет</h3>
                <p>Район: Верхний Джал, жаңы ремонт</p>
                <p>2 балкон, 2 лифт</p>
                <div class="btn-group">
                    <a href="tel:+996703014940" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996703014940" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">20 000 сом</div>
                <h3>Жер там комната берилет / Сдается комната в доме</h3>
                <p>Кок-Жар ж/м, жаш үй-бүлө же кыздарга</p>
                <p>Ысык муздак суу, Wi-Fi, холодильник</p>
                <div class="btn-group">
                    <a href="tel:+996504122122" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996504122122" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Комната">
                <div class="price">15 000 сом</div>
                <h3>Сдаётся квартира / Квартира берилет</h3>
                <p>ул. Интергельпо, дом 15, душ жок</p>
                <p>Туалет короодо</p>
                <div class="btn-group">
                    <a href="tel:+996553112350" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996553112350" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">30 000 сом</div>
                <h3>Сдаю 1 комнатную квартиру / 1 бөлмөлүү квартира берилет</h3>
                <p>6 мкр, 1 этаж, евроремонт</p>
                <p>Бардык шарттар бар</p>
                <div class="btn-group">
                    <a href="tel:+996702558333" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996702558333" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">20 000 сом</div>
                <h3>Частный домдон квартира берилет / Сдается квартира из частного дома</h3>
                <p>Дордой базар, Келечек</p>
                <p>Эки кишиге же үй-бүлө</p>
                <div class="btn-group">
                    <a href="tel:+996502065646" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996502065646" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">23 000 сом</div>
                <h3>Кара жыгачтан времянка квартира / Временная квартира из дерева</h3>
                <p>Жаш үй-бүлө үчүн, ысык суу, душ бар</p>
                <div class="btn-group">
                    <a href="tel:+996700959598" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996700959598" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Дом">
                <div class="price">35 000 сом</div>
                <h3>Сдаю дом 2 комната / 2 бөлмөлүү үй берилет</h3>
                <p>Район: Кызыл Аскер, ул. Осташковская 10</p>
                <p>Чоң огород бар</p>
                <div class="btn-group">
                    <a href="tel:+996709150190" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996709150190" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Дом">
                <div class="price">22 000 сом</div>
                <h3>Сдаю пол дома без хозяина / Жарым үй берилет, хозяин жок</h3>
                <p>Ванна, туалет, газ бар</p>
                <div class="btn-group">
                    <a href="tel:+996700060958" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996700060958" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Студия">
                <div class="price">30 000 сом, депозит 5 000 сом</div>
                <h3>Сдаётся студия / Студия берилет</h3>
                <p>Район: Восток-5, жеке сектор</p>
                <p>Жаңы, бардык шарттар бар</p>
                <div class="btn-group">
                    <a href="tel:+996507897099" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996507897099" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Дом">
                <div class="price">45 000 сом</div>
                <h3>Сдаётся большой дом / Чоң үй берилет</h3>
                <p>Район: ул. Коммунаров, 102 жана 266 маршрут</p>
                <p>4 бөлмө, жылуу, кирпич</p>
                <div class="btn-group">
                    <a href="tel:+996705035010" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996705035010" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">30 000 сом + 20 000 депозит</div>
                <h3>Сдаются квартиры / Квартиралар берилет</h3>
                <p>Кызыл Аскер, ул. 9 января</p>
                <p>3 квартира, парковка бар</p>
                <div class="btn-group">
                    <a href="tel:+996709144166" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996709144166" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">31 000 сом</div>
                <h3>Сдаю квартиру 2х комнатную / 2 бөлмөлүү квартира берилет</h3>
                <p>Ж/м Алтын Ордо, ул. Горького 4/47</p>
                <p>Коммуналдык төлөмдөр кирет</p>
                <div class="btn-group">
                    <a href="tel:+996505511117" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996505511117" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Общежитие">
                <div class="price">17 000 сом</div>
                <h3>Сдаю 1 ком общежития / 1 бөлмөлүү общежитие берилет</h3>
                <p>Восток-5 мкр, 18 м², душ туалет орток</p>
                <div class="btn-group">
                    <a href="tel:+996704312879" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996704312879" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">35 000 сом</div>
                <h3>Сдаю 1 ком. кв / 1 бөлмөлүү квартира берилет</h3>
                <p>8 мкр, 3 этаж, Советскаяга чыгуучу</p>
                <p>Жаңы ремонт, мебель жана техникалар</p>
                <div class="btn-group">
                    <a href="tel:+996550503430" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996550503430" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">39 000 сом, депозит 20 000 сом</div>
                <h3>Срочно сдается новая 2 к квартира студия / Жаңы 2 бөлмөлүү студия берилет</h3>
                <p>Адрес: Чортекова / Куюкова</p>
                <p>С мебелью, чыныгыларга</p>
                <div class="btn-group">
                    <a href="tel:+996501150589" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996501150589" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">30 000 сом</div>
                <h3>Сдается 1 - комнатная квартира / 1 бөлмөлүү квартира берилет</h3>
                <p>Район: Рабочий городок, ул. Гагарина / Т. Фрунзе</p>
                <p>2/2 этаж, бардык шарттар</p>
                <div class="btn-group">
                    <a href="tel:+996550120676" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996550120676" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Студия">
                <div class="price">32 000 сом</div>
                <h3>Сдам 1 комнатную студию / 1 бөлмөлүү студия берилет</h3>
                <p>Рабочий городок, Чапаева Гагарина</p>
                <p>Евроремонт, бардык шарттар</p>
                <div class="btn-group">
                    <a href="tel:+996707363666" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996707363666" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">39 000 сом, депозит 20 000 сом</div>
                <h3>Срочно сдается новая 1 к квартира / Жаңы 1 бөлмөлүү квартира берилет</h3>
                <p>Адрес: Чортекова / Куюкова</p>
                <p>С мебелью, чыныгыларга</p>
                <div class="btn-group">
                    <a href="tel:+996501150589" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996501150589" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">45 000 сом</div>
                <h3>Сдается 3 комнатная квартира / 3 бөлмөлүү квартира берилет</h3>
                <p>11 мкр, 104 серия, 4 этаж</p>
                <p>Только семейным</p>
                <div class="btn-group">
                    <a href="tel:+996555628864" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996555628864" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">37 000 сом</div>
                <h3>Сдаю 1 комнатную квартиру / 1 бөлмөлүү квартира берилет</h3>
                <p>Душанбинка/Айни, узак мөөнөткө</p>
                <p>3 ай алдын ала төлөм</p>
                <div class="btn-group">
                    <a href="tel:+996999800088" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996999800088" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">25 000 сом + 10 000 депозит</div>
                <h3>Сдаю 1-комнатную квартиру / 1 бөлмөлүү квартира берилет</h3>
                <p>ул. Алматинка / Салиева</p>
                <p>Бардык техникалар бар</p>
                <div class="btn-group">
                    <a href="tel:+996504108633" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996504108633" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">33 000 сом</div>
                <h3>Сдается 1-комнатная квартира / 1 бөлмөлүү квартира берилет</h3>
                <p>Белинский Жибек Жолу, 3 этаж</p>
                <p>Бардык ыңгайлуулуктар бар</p>
                <div class="btn-group">
                    <a href="tel:+996709046967" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996709046967" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">30 000 сом + 20 000 депозит</div>
                <h3>Сдаются 2-х комнатные квартиры / 2 бөлмөлүү квартиралар берилет</h3>
                <p>Кызыл Аскер, ул. 9 января</p>
                <p>Жаңы үй, парковка бар</p>
                <div class="btn-group">
                    <a href="tel:+996709144166" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996709144166" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">20 000 сом</div>
                <h3>Частный домдон квартира берилет / Сдается квартира из частного дома</h3>
                <p>Дордой базар, Келечек</p>
                <p>Эки кишиге же үй-бүлө</p>
                <div class="btn-group">
                    <a href="tel:+996502065646" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996502065646" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Дом">
                <div class="price">40 000 сом</div>
                <h3>Сдается 2х комнатный + кухня дом / 2 бөлмөлүү + ашканасы бар үй берилет</h3>
                <p>Азия Молл районы, 74 мектепке жакын</p>
                <div class="btn-group">
                    <a href="tel:+996501899093" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996501899093" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">16 000 сом, депозит 8 000 сом</div>
                <h3>Сдается 1 ком кв / 1 бөлмөлүү квартира берилет</h3>
                <p>Район: Таатан, ТЭЦ, жеке санузел</p>
                <p>Жарык счетчикке ылайык</p>
                <div class="btn-group">
                    <a href="tel:+996703985033" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996703985033" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">20 000 сом</div>
                <h3>Сдаю двух комнатную квартиру / 2 бөлмөлүү квартира берилет</h3>
                <p>Дордой, ул. Советская / Зеленая</p>
                <p>Евроремонт, санузел орток</p>
                <div class="btn-group">
                    <a href="tel:+996704263473" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996704263473" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">20 000 сом</div>
                <h3>Сдается квартира гостининого типа / Гостини типтеги квартира берилет</h3>
                <p>Ж/м Ак-Ордо, ул. Сыпайы 5, со всеми условиями</p>
                <p>Коммуналдык төлөмдөр кирет</p>
                <div class="btn-group">
                    <a href="tel:+996706811007" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996706811007" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">21 000 сом</div>
                <h3>Сдаю малосемей на 2 чел / 2 киши үчүн малосемей берилет</h3>
                <p>Ак Орго, 84 мектеп, жаңы ремонт</p>
                <p>Бардык шарттар бар</p>
                <div class="btn-group">
                    <a href="tel:+996700418481" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996700418481" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">25 000 сом</div>
                <h3>Сдаю 1 комнатную квартиру / 1 бөлмөлүү квартира берилет</h3>
                <p>Рынок Кудайберген</p>
                <div class="btn-group">
                    <a href="tel:+996550992500" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996550992500" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">50 000 сом</div>
                <h3>Сдается 2х комнатная квартира / 2 бөлмөлүү квартира берилет</h3>
                <p>7 мкр, жаңы ремонт, бардык шарттар</p>
                <p>Только чыныгы үй-бүлө</p>
                <div class="btn-group">
                    <a href="tel:+996707330075" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996707330075" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">10 000 сом</div>
                <h3>Сдается квартира / Квартира берилет</h3>
                <p>Район: Кудайберген, цокольный этаж</p>
                <div class="btn-group">
                    <a href="tel:+996550821001" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996550821001" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">25 000 сом</div>
                <h3>Сдаю 1-комнатную квартиру / 1 бөлмөлүү квартира берилет</h3>
                <p>Рынок Кудайберген, собственник</p>
                <div class="btn-group">
                    <a href="tel:+996700102573" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996700102573" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">35 000 сом</div>
                <h3>Сдаю 1 комнатная квартира / 1 бөлмөлүү квартира берилет</h3>
                <p>Дордой Плаза, Чуй Гоголя</p>
                <p>Только парни же кыздар</p>
                <div class="btn-group">
                    <a href="tel:+996770020357" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996770020357" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">23 000 сом</div>
                <h3>Квартира берилет / Сдается квартира</h3>
                <p>Рухий Мурас, кыздарга 2-3</p>
                <p>Бардык шарттар, 6 автобус</p>
                <div class="btn-group">
                    <a href="tel:+996708372536" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996708372536" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">28 000 сом</div>
                <h3>Сдаю 1к квартиру / 1 бөлмөлүү квартира берилет</h3>
                <p>Ахунбаева Репина, жеке кирүү</p>
                <p>Бардык техникалар жана мебель</p>
                <div class="btn-group">
                    <a href="tel:+996702980598" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996702980598" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Студия">
                <div class="price">22 000 сом</div>
                <h3>Сдается студия / Студия берилет</h3>
                <p>Западный автовокзал, жаңы ремонт</p>
                <p>24 м², студенттер же паре</p>
                <div class="btn-group">
                    <a href="tel:+996755236287" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996755236287" class="contact-btn">WhatsApp</a>
                </div>
            </div>
            <div class="card">
                <img src="https://tgram.uz/uploads/channels/18/2805458338f33426ddf6be5e8ac9f75f.jpg" alt="Квартира">
                <div class="price">25 000 сом</div>
                <h3>Квартира гостиного типа берилет / Сдается квартира гостиного типа</h3>
                <p>Баткенский рынок, бардык коммуналдык ичинде</p>
                <div class="btn-group">
                    <a href="tel:+996500814002" class="contact-btn">Звонок</a>
                    <a href="https://wa.me/+996500814002" class="contact-btn">WhatsApp</a>
                </div>
            </div>
        </div>
    </div>
    <button class="admin-btn" onclick="alert('Саламатсызбы! Атым Romka, сайт түзүүчүсү болом. Эгерде кандайдыр бир көйгөй жаралса, мага кайрылууңуз болот.'); window.location.href='https://wa.me/+996504589189?text=Саламатсызбы%20Romka,%20сайт%20туралу%20жазып%20жатабыз';">Администратор менен байланышуу</button>

    <script>
        document.body.style.overflow = 'hidden';
        document.getElementById('warningMessage').style.display = 'block';

        function changeLanguage(lang) {
            const elements = document.getElementsByTagName('*');
            if (lang === 'ky') {
                document.querySelector('.header h1').textContent = 'Квартира Издөө Сайты';
                document.querySelector('.warning p:nth-child(1)').textContent = 'Саламатсызбы, колдонуучу! Сиздин коопсуздугуңуз үчүн эскертебиз: Квартира боюнча онлайн сүйлөшүүдө акча которбоңуз. Квартираны өзүңүз көрүп, толук маалымат алгандан кийин гана, ишенимдүү болсо, келишим түзүңүз.';
                document.querySelector('.warning button').textContent = 'Макул';
                document.querySelector('#agreement p:nth-child(1)').textContent = 'Саламатсызбы, колдонуучу! Сиздин коопсуздугуңуз үчүн эскертебиз: Квартира боюнча онлайн сүйлөшүүдө акча которбоңуз. Квартираны өзүңүз көрүп, толук маалымат алгандан кийин гана, ишенимдүү болсо, келишим түзүңүз.';
                document.querySelector('#agreement button').textContent = 'Макул';
            } else if (lang === 'ru') {
                document.querySelector('.header h1').textContent = 'Сайт Поиска Квартир';
                document.querySelector('.warning p:nth-child(1)').textContent = 'Здравствуйте, пользователь! Для вашей безопасности предупреждаем: Не переводите деньги онлайн при обсуждении квартиры. Осмотрите квартиру лично и получите полную информацию, заключайте сделку только при полной уверенности.';
                document.querySelector('.warning button').textContent = 'Согласен';
                document.querySelector('#agreement p:nth-child(1)').textContent = 'Здравствуйте, пользователь! Для вашей безопасности предупреждаем: Не переводите деньги онлайн при обсуждении квартиры. Осмотрите квартиру лично и получите полную информацию, заключайте сделку только при полной уверенности.';
                document.querySelector('#agreement button').textContent = 'Согласен';
            }
        }
    </script>
</body>
</html>
