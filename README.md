
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>全球畫廊展覽總覽 · 2026年5月</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'Helvetica Neue', Arial, 'PingFang TC', 'Noto Sans TC', sans-serif;
      background: #f5f4f0;
      color: #1a1a1a;
      min-height: 100vh;
    }

    header {
      background: #1a1a1a;
      color: #fff;
      padding: 40px 48px 32px;
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      flex-wrap: wrap;
      gap: 16px;
    }

    header h1 {
      font-size: 28px;
      font-weight: 300;
      letter-spacing: 0.04em;
    }

    header .meta {
      font-size: 12px;
      color: #888;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .controls {
      background: #fff;
      border-bottom: 1px solid #e0e0e0;
      padding: 16px 48px;
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .controls input[type="text"] {
      flex: 1;
      min-width: 200px;
      padding: 8px 14px;
      border: 1px solid #ddd;
      border-radius: 4px;
      font-size: 14px;
      outline: none;
      transition: border-color 0.2s;
    }

    .controls input[type="text"]:focus {
      border-color: #1a1a1a;
    }

    .filter-btn {
      padding: 8px 16px;
      border: 1px solid #ddd;
      border-radius: 4px;
      background: #fff;
      font-size: 13px;
      cursor: pointer;
      transition: all 0.15s;
      white-space: nowrap;
    }

    .filter-btn:hover { background: #f0f0f0; }
    .filter-btn.active { background: #1a1a1a; color: #fff; border-color: #1a1a1a; }

    .count {
      margin-left: auto;
      font-size: 12px;
      color: #888;
      white-space: nowrap;
    }

    main {
      padding: 32px 48px 64px;
      max-width: 1400px;
      margin: 0 auto;
    }

    .region-section { margin-bottom: 48px; }

    .region-label {
      font-size: 11px;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: #888;
      font-weight: 500;
      margin-bottom: 16px;
      padding-bottom: 8px;
      border-bottom: 1px solid #e0e0e0;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 16px;
    }

    .card {
      background: #fff;
      border: 1px solid #e8e8e8;
      border-radius: 6px;
      padding: 22px 22px 18px;
      display: flex;
      flex-direction: column;
      gap: 8px;
      transition: box-shadow 0.2s, transform 0.15s;
      cursor: default;
    }

    .card:hover {
      box-shadow: 0 4px 20px rgba(0,0,0,0.08);
      transform: translateY(-2px);
    }

    .card-top {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      gap: 8px;
    }

    .gallery-name {
      font-size: 10px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: #888;
      font-weight: 500;
    }

    .location-tag {
      font-size: 10px;
      color: #aaa;
      white-space: nowrap;
    }

    .artist-name {
      font-size: 16px;
      font-weight: 600;
      line-height: 1.3;
      color: #1a1a1a;
    }

    .exhibition-title {
      font-size: 13px;
      color: #555;
      font-style: italic;
      line-height: 1.4;
    }

    .dates {
      font-size: 11px;
      color: #999;
      margin-top: 2px;
    }

    .description {
      font-size: 12px;
      color: #666;
      line-height: 1.7;
      margin-top: 4px;
      flex: 1;
    }

    .card-footer {
      margin-top: 12px;
      padding-top: 10px;
      border-top: 1px solid #f0f0f0;
    }

    .card-footer a {
      font-size: 11px;
      color: #1a1a1a;
      text-decoration: none;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      display: inline-flex;
      align-items: center;
      gap: 4px;
      opacity: 0.5;
      transition: opacity 0.15s;
    }

    .card-footer a:hover { opacity: 1; }

    .card-footer a::after {
      content: '→';
      font-size: 11px;
    }

    .hidden { display: none !important; }

    .empty-state {
      text-align: center;
      padding: 80px 20px;
      color: #aaa;
      font-size: 14px;
      grid-column: 1 / -1;
    }

    .region-section.empty { display: none; }

    @media (max-width: 768px) {
      header, .controls, main { padding-left: 20px; padding-right: 20px; }
      header h1 { font-size: 22px; }
      .grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

<header>
  <div>
    <h1>全球畫廊展覽總覽</h1>
  </div>
  <div class="meta">更新於 2026年5月9日 &nbsp;·&nbsp; 25 個畫廊 &nbsp;·&nbsp; 54 個展覽</div>
</header>

<div class="controls">
  <input type="text" id="search" placeholder="搜尋藝術家、展覽、畫廊…" oninput="filterCards()">
  <button class="filter-btn active" onclick="setRegion('全部')">全部</button>
  <button class="filter-btn" onclick="setRegion('亞洲')">亞洲</button>
  <button class="filter-btn" onclick="setRegion('歐洲')">歐洲</button>
  <button class="filter-btn" onclick="setRegion('美洲')">美洲</button>
  <span class="count" id="count"></span>
</div>

<main id="main">
  <!-- 亞洲 -->
  <div class="region-section" data-region="亞洲">
    <div class="region-label">亞洲</div>
    <div class="grid" id="grid-亞洲"></div>
  </div>
  <!-- 歐洲 -->
  <div class="region-section" data-region="歐洲">
    <div class="region-label">歐洲</div>
    <div class="grid" id="grid-歐洲"></div>
  </div>
  <!-- 美洲 -->
  <div class="region-section" data-region="美洲">
    <div class="region-label">美洲</div>
    <div class="grid" id="grid-美洲"></div>
  </div>
</main>

<script>
const exhibitions = [{"gallery":"Kukje Gallery","location":"首爾","region":"亞洲","artist":"朴贊景 Park Chan-Kyong","title":"Zen Master of the Eyeball","dates":"2026年3月19日 – 5月10日","description":"韓國藝術家朴贊景在國際畫廊首爾K1空間展出約二十幅近作繪畫。朴贊景長期探索韓國現代史、殖民創傷與集體記憶，以影像、裝置與繪畫語言審視觀看行為本身的政治性與哲學意涵，此次展覽以「眼球禪師」為題深入探討凝視的倫理問題。","url":"https://www.kukjegallery.com/"},{"gallery":"Kukje Gallery","location":"首爾","region":"亞洲","artist":"Lotus L. Kang","title":"Chora","dates":"2026年3月19日 – 5月10日","description":"Lotus L. Kang於國際畫廊首爾K3空間展出個展「Chora」。藝術家以跨媒材實踐探索身體、物質與空間的關係，借用古希臘哲學概念「Chora」——既非存在也非虛無的模糊領域——思考當代身分認同與生命政治議題，呈現流動身份的詩意想象。","url":"https://www.kukjegallery.com/"},{"gallery":"Ota Fine Arts","location":"東京","region":"亞洲","artist":"島田淑子 Yoshiko Shimada","title":"Selfless Devotion / Loving Care","dates":"2026年3月14日 – 5月16日","description":"日本藝術家島田淑子於OTA Fine Arts東京空間展出個展，呈現「Past Imperfect」系列作品，聚焦二戰期間日本女性的戰時動員與護理照料歷史，通過刺繡、文件與圖像媒材反思戰爭中的性別政治與被壓抑的集體記憶。","url":"https://www.otafinearts.com/"},{"gallery":"Ota Fine Arts","location":"上海","region":"亞洲","artist":"陳維、崔潔、Yasmine Anlan Huang、那布其、Guo-Liang Tan、張如怡","title":"群展","dates":"2026年3月19日 – 5月30日","description":"OTA Fine Arts上海空間呈現六位亞洲當代藝術家群展，參展者包括陳維、崔潔、Yasmine Anlan Huang、那布其、Guo-Liang Tan及張如怡，作品涵蓋攝影、繪畫、雕塑等媒材，呈現新生代亞洲藝術家對都市文化與身份認同的多元觀察。","url":"https://www.otafinearts.com/"},{"gallery":"Tomio Koyama Gallery","location":"東京","region":"亞洲","artist":"廣瀬智央 Satoshi Hirose","title":"個展","dates":"2026年4月1日 – 5月31日","description":"日本藝術家廣瀬智央於小山登美夫畫廊展出個展。廣瀬長期以概念裝置探索自然、時間與語言的交叉地帶，以種子、香料等日常物質呈現文化交流與生命循環的哲學思考，是日本當代藝術中跨文化對話的重要實踐者。","url":"https://www.tomiokoyamagallery.com/"},{"gallery":"Tomio Koyama Gallery","location":"東京","region":"亞洲","artist":"蜷川實花 Mika Ninagawa","title":"個展","dates":"2026年3月13日 – 5月31日","description":"日本知名攝影師與電影導演蜷川實花於小山登美夫畫廊舉辦個展，展出其標誌性的鮮豔色彩攝影作品。蜷川以濃烈的視覺語言聞名，常以花卉、金魚與霓虹光影構成超現實的夢幻場景，探索美麗、消逝與日本當代流行文化。","url":"https://www.tomiokoyamagallery.com/"},{"gallery":"Whitestone Gallery","location":"東京","region":"亞洲","artist":"藤原紫保 Shiho Fujiwara","title":"Living Through Paper: The Trajectory of Shiho Fujiwara's 'Line'","dates":"2026年4月10日 – 5月2日","description":"日本藝術家藤原紫保於白石畫廊東京空間展出個展，聚焦其以「線」為核心的藝術實踐歷程。藤原長期以紙張為媒介進行線條探索，展覽回顧並呈現其創作軌跡中對材質、空間與身體關係的深刻思考，以紙性之脆弱反映生命的韌性。","url":"https://whitestonegallery.com/"},{"gallery":"Whitestone Gallery","location":"首爾","region":"亞洲","artist":"群展","title":"A Swimming Soul","dates":"2026年4月18日 – 5月24日","description":"白石畫廊首爾空間呈現群展「游泳的靈魂」，探索藝術創作中情感流動與精神自由的主題，匯聚多位藝術家的繪畫、雕塑與裝置作品，以「泳動」作為隱喻，呈現藝術家在各自文化脈絡中尋求精神解放的共同渴望。","url":"https://whitestonegallery.com/"},{"gallery":"Hauser & Wirth","location":"香港","region":"亞洲","artist":"群展","title":"Fallen Angels","dates":"2026年3月24日 – 5月30日","description":"豪瑟與沃斯香港空間呈現群展「墮落天使」，匯聚多位國際藝術家的作品，探索神話敘事中墮落、救贖與超越的主題，以「天使」的文化原型為切入點，呈現當代藝術家對精神信仰、道德邊界與人類處境的多元詮釋。","url":"https://www.hauserwirth.com/"},{"gallery":"White Cube","location":"首爾","region":"亞洲","artist":"Takis & Nam June Paik","title":"Duett","dates":"2026年5月2日 – 6月5日","description":"白立方首爾空間呈現希臘雕塑家塔基斯與韓裔美國錄像藝術先驅白南準的雙人展「二重奏」，兩位藝術家均對電磁能量與科技媒材情有獨鍾，展覽以「二重奏」之名呈現兩種截然不同卻相互呼應的能量藝術詩學。","url":"https://www.whitecube.com/"},{"gallery":"Perrotin","location":"巴黎","region":"歐洲","artist":"Lee Mingwei","title":"When Beauty Appears","dates":"2026年4月25日 – 5月30日","description":"台裔美國藝術家李明維於貝浩登巴黎空間舉辦個展，呈現其探索連結、姿態與儀式的藝術實踐。李明維以關係美學聞名，作品常邀請觀眾參與，化日常互動為詩意的藝術體驗，深入探討美的當下性與人際間的精神交流。","url":"https://www.perrotin.com/"},{"gallery":"Perrotin","location":"巴黎","region":"歐洲","artist":"Susumu Kamijo","title":"When I Think of You in Spring","dates":"2026年4月25日 – 5月30日","description":"日本藝術家上條朔於貝浩登巴黎空間展出個展，以花卉與動物為主題呈現細膩溫柔的繪畫世界。上條的作品介於自然觀察與想象之間，以精緻的東方美學語言描繪春日的靜謐詩意，表達對自然界生命循環的深切感懷。","url":"https://www.perrotin.com/"},{"gallery":"Gagosian","location":"巴黎","region":"歐洲","artist":"Francis Bacon","title":"Francis Bacon","dates":"2026年4月11日 – 5月30日","description":"高古軒巴黎卡斯蒂廖涅街空間呈現英國藝術大師弗朗西斯·培根的重要展覽。培根以扭曲變形的人體繪畫聞名於世，作品充滿存在主義的焦慮與肉身的脆弱感，此次展覽呈現其對人類處境的深刻審視與獨特的表現主義繪畫語言。","url":"https://gagosian.com/"},{"gallery":"Hauser & Wirth","location":"倫敦","region":"歐洲","artist":"Roni Horn","title":"Seizure of Hope","dates":"2026年5月21日 – 8月1日","description":"美國概念藝術家羅妮·霍恩於豪瑟與沃斯倫敦空間舉辦個展「希望的驟奪」。霍恩以裝置、攝影及文字探索身份的流動性、水的哲學隱喻及性別政治，作品拒絕固定的詮釋框架，邀請觀者在物質與語言的臨界地帶尋找個體存在的意義。","url":"https://www.hauserwirth.com/"},{"gallery":"Hauser & Wirth","location":"巴塞爾","region":"歐洲","artist":"Niklaus Stoecklin","title":"個展","dates":"2026年3月19日 – 5月23日","description":"瑞士現代主義藝術家尼克勞斯·施托克林於豪瑟與沃斯巴塞爾空間展出重要個展。施托克林以精緻的新即物主義繪畫風格聞名，尤擅海報設計與寫實人物，此次展覽重新審視這位二十世紀初瑞士藝術史中被低估的視覺語言革新者。","url":"https://www.hauserwirth.com/"},{"gallery":"David Zwirner","location":"巴黎","region":"歐洲","artist":"Mamma Andersson","title":"Œuvres sur papier","dates":"2026年4月23日 – 6月27日","description":"瑞典藝術家瑪瑪·安德森於卓納畫廊巴黎空間展出紙上作品個展。安德森以豐富的北歐神話、民間傳說與日常生活場景為素材，以獨特的敘事繪畫風格享譽國際，此次展覽呈現其創作過程的即興性與詩意想象力。","url":"https://www.davidzwirner.com/"},{"gallery":"David Zwirner","location":"倫敦","region":"歐洲","artist":"Dan Flavin, Donald Judd, John McCracken, Robert Ryman, Fred Sandback","title":"Flavin, Judd, McCracken, Ryman, Sandback","dates":"2026年3月25日 – 5月22日","description":"卓納畫廊倫敦空間呈現五位極簡主義藝術大師的群展，匯聚弗拉文、賈德、麥克拉肯、賴曼與桑德貝克的代表性作品，系統梳理二十世紀後期美國極簡主義藝術運動的核心視覺語言與哲學理念。","url":"https://www.davidzwirner.com/"},{"gallery":"White Cube","location":"倫敦","region":"歐洲","artist":"Katharina Grosse","title":"I Set Out, I Walked Fast","dates":"2026年4月22日 – 5月31日","description":"德國藝術家卡塔琳娜·葛羅斯於白立方倫敦百蒙德賽空間展出大型裝置個展。葛羅斯以噴槍創作大規模色彩噴繪著稱，作品突破畫布邊界蔓延至建築表面，延續其對繪畫邊界與空間時間性的激進探索，以行走動作隱喻藝術創作的身體性。","url":"https://www.whitecube.com/"},{"gallery":"White Cube","location":"巴黎","region":"歐洲","artist":"朴栖甫 Park Seo-Bo","title":"Ecritures","dates":"2026年4月15日 – 5月30日","description":"韓國丹青畫大師朴栖甫於白立方巴黎空間展出其標誌性「書寫」系列，為「報紙書寫」作品首次於巴黎公開展覽。朴栖甫以冥想性的重複線條構建極簡而深邃的視覺語言，是韓國單色畫（丹青畫）運動的開創性人物。","url":"https://www.whitecube.com/"},{"gallery":"Victoria Miro","location":"倫敦","region":"歐洲","artist":"Paula Rego","title":"Story Line","dates":"2026年4月16日 – 5月23日","description":"葡萄牙裔英國藝術家寶拉·雷戈於維多利亞·米羅畫廊倫敦一館展出迄今最全面的素描回顧展。雷戈以充滿敘事張力的人物繪畫揭示女性處境、童年創傷與社會不公，此次展覽聚焦「線條」作為其藝術語言演化核心。","url":"https://www.victoria-miro.com/"},{"gallery":"Victoria Miro","location":"倫敦","region":"歐洲","artist":"Yulia Iosilzon","title":"個展","dates":"2026年4月15日 – 5月31日","description":"俄羅斯裔英國藝術家尤利婭·伊奧希爾宗於維多利亞·米羅畫廊Miro Presents空間展出新繪畫與陶瓷作品，以夢幻般的色彩與變形的圖像探索存在的流動性，作品中人物與風景處於持續的形態轉化之中，呈現內在世界的詩意流動。","url":"https://www.victoria-miro.com/"},{"gallery":"Lehmann Maupin","location":"倫敦","region":"歐洲","artist":"Anna Park","title":"個展","dates":"2026年4月30日 – 5月30日","description":"韓裔美國藝術家安娜·帕克於利曼慕平倫敦梅費爾新空間舉辦其加入畫廊後的首次個展，亦是其英國首次個展。帕克以大尺幅黑白炭筆繪畫聞名，以汪洋恣肆的線條描繪人群與身體，呈現當代社會喧囂下潛藏的孤獨感。","url":"https://www.lehmannmaupin.com/"},{"gallery":"Galerie Thaddaeus Ropac","location":"巴黎","region":"歐洲","artist":"群展","title":"Roman Campagna: New Paintings and Drawings","dates":"2026年4月18日 – 5月30日","description":"塔德烏斯·羅帕克畫廊巴黎瑪黑空間呈現以羅馬鄉間為主題的新作繪畫與素描群展，探索古典義大利風景在當代藝術中的再詮釋，呈現多位藝術家如何在傳統風景畫脈絡中注入當代視角，重新召喚義大利鄉土的詩意想象。","url":"https://ropac.net/"},{"gallery":"Galerie Thaddaeus Ropac","location":"倫敦","region":"歐洲","artist":"群展","title":"Listening + Looking","dates":"2026年4月10日 – 5月23日","description":"塔德烏斯·羅帕克畫廊倫敦艾利之屋空間展出「聆聽與觀看」群展，探索聲音藝術、視覺藝術與多感官體驗的交匯地帶，邀請觀眾反思視覺凝視與聆聽感知的差異，以及藝術作品如何同時訴諸多種感官維度觸動觀者。","url":"https://ropac.net/"},{"gallery":"Marian Goodman Gallery","location":"巴黎","region":"歐洲","artist":"Ettore Spalletti & Dan Graham","title":"Ettore Spalletti And Dan Graham","dates":"2026年4月17日 – 6月20日","description":"馬里安·古德曼畫廊巴黎空間呈現義大利藝術家埃托爾·斯帕萊蒂與美國概念藝術家丹·格雷厄姆的雙人展，探索兩位藝術家在色彩、光線、空間與建築議題上的深層對話，以及截然不同的媒材語言如何呈現相似的哲學關懷。","url":"https://www.mariangoodman.com/"},{"gallery":"Almine Rech","location":"巴黎","region":"歐洲","artist":"群展","title":"Forming the Monochrome: Masters of Dansaekhwa","dates":"2026年3月21日 – 5月23日","description":"艾敏·雷克畫廊巴黎Matignon空間呈現韓國單色畫（丹青畫）大師群展，聚焦這一韓國當代藝術運動的核心美學精神，以重複的身體行為、物質性探索與東方哲學為基礎，系統呈現丹青畫運動的形成過程及對國際藝術史的重要貢獻。","url":"https://www.alminerech.com/"},{"gallery":"Sadie Coles HQ","location":"倫敦","region":"歐洲","artist":"Wilhelm Sasnal","title":"family / history","dates":"2026年4月1日 – 5月23日","description":"波蘭藝術家威廉·薩斯納爾於薩迪·科爾斯畫廊薩維爾街空間展出新繪畫個展「家庭/歷史」。薩斯納爾的作品以日常生活圖像和波蘭歷史事件為題材，展覽呈現私人記憶與公共歷史的緊密交織，以繪畫語言探索記憶的政治性。","url":"https://www.sadiecoles.com/"},{"gallery":"Sadie Coles HQ","location":"倫敦","region":"歐洲","artist":"Seth Price","title":"Redistribution 2026–2007","dates":"2026年3月17日 – 5月16日","description":"美國藝術家賽斯·普萊斯於薩迪·科爾斯畫廊金利街空間展出個展，以逆序標題點明其創作的時間回溯性。普萊斯以挪用、複製與再分配文化材料著稱，探索媒體流通與資本主義文化生產機制，展覽梳理其近二十年的創作脈絡。","url":"https://www.sadiecoles.com/"},{"gallery":"Sprüth Magers","location":"倫敦","region":"歐洲","artist":"Thomas Scheibitz","title":"Bright Shadows","dates":"2026年4月10日 – 5月16日","description":"德國藝術家托馬斯·謝比茨於施普魯斯·馬格斯倫敦空間展出個展「明亮陰影」，呈現其跨越2017年至今的新舊作品，以獨特的「圖形繪畫」融合符號學、建築語彙與流行文化圖像，構建介於具象與抽象之間的視覺謎題。","url":"https://spruethmagers.com/"},{"gallery":"Sprüth Magers","location":"柏林","region":"歐洲","artist":"Richard Artschwager & Gary Hume","title":"Richard Artschwager / Gary Hume","dates":"2026年4月15日 – 5月22日","description":"施普魯斯·馬格斯柏林空間首次將美國藝術家理查德·阿茨瓦格與英國藝術家蓋瑞·休姆的作品並置展出，探索兩位藝術家在極簡主義影響下如何以截然不同的方式處理物件性與表面性的藝術問題。","url":"https://spruethmagers.com/"},{"gallery":"König Galerie","location":"柏林","region":"歐洲","artist":"Clédia Fourniau","title":"個展","dates":"2026年5月1日 – 5月31日","description":"法國藝術家克萊迪亞·富爾尼奧於柯尼希畫廊聖阿格尼斯空間舉辦第三次個展，帶來新繪畫系列及首次亮相的紙上作品，以「交換」的姿態為核心，探索動作起始的瞬間與期待回應之間的詩意張力。","url":"https://www.koeniggalerie.com/"},{"gallery":"König Galerie","location":"柏林","region":"歐洲","artist":"Joana Schneider","title":"EEUWEN","dates":"2026年3月13日 – 5月30日","description":"德國藝術家喬安娜·施耐德於柯尼希畫廊電報局空間展出個展「世紀」，以漁網等海洋廢棄材料製作的精細纖維裝置著稱，將海洋廢棄物轉化為藝術語言，深入探索材料的時間性、海洋生態與工藝傳統的當代意義。","url":"https://www.koeniggalerie.com/"},{"gallery":"Galerie Eva Presenhuber","location":"蘇黎世","region":"歐洲","artist":"Valentin Carron","title":"The Slope (Works 2005–2026)","dates":"2026年2月26日 – 7月10日","description":"瑞士藝術家瓦倫丁·卡隆於Eva Presenhuber畫廊展出跨越二十年的創作回顧展，以挪用地方民俗符號與公共裝飾物著稱，以雕塑與裝置媒介質疑藝術的正典性，系統梳理其對傳統、地方性與當代藝術體制的批判性思考。","url":"https://www.presenhuber.com/"},{"gallery":"Galerie Eva Presenhuber","location":"蘇黎世","region":"歐洲","artist":"Aria Dean, Sandra Mujinga, Tschabalala Self","title":"群展","dates":"2026年3月28日 – 5月23日","description":"Eva Presenhuber畫廊Waldmannstrasse空間呈現三位藝術家阿里亞·迪恩、桑德拉·穆欽加與謝巴拉拉·賽爾夫的群展，三位藝術家以影像、雕塑與繪畫分別探索身份認同、技術政治與具身性的多元面向。","url":"https://www.presenhuber.com/"},{"gallery":"Galerie Chantal Crousel","location":"巴黎","region":"歐洲","artist":"Lydia Ourahmane","title":"1752 Photos","dates":"2026年 – 5月28日","description":"阿爾及利亞藝術家莉迪亞·烏拉馬訥於香塔爾·克魯塞爾畫廊巴黎空間展出個展「1752張照片」，以攝影、聲音與裝置跨媒材探索政治邊界、移民經歷與非洲現代歷史，以大量攝影作品揭示被官方敘事遮蔽的個人與集體記憶。","url":"https://www.crousel.com/"},{"gallery":"Xavier Hufkens","location":"布魯塞爾","region":"歐洲","artist":"Joan Semmel","title":"Continuities","dates":"2026年 – 6月27日","description":"美國女性主義藝術家瓊·塞梅爾於澤維爾·胡夫肯斯畫廊布魯塞爾Rivoli空間展出個展「延續」，以大膽的女性裸體自畫像聞名，以第一視角呈現女性對自身身體的主動凝視，展覽涵蓋其跨越數十年的重要繪畫。","url":"https://www.xavierhufkens.com/"},{"gallery":"Xavier Hufkens","location":"布魯塞爾","region":"歐洲","artist":"Nicolas Party","title":"Toile d'araignée","dates":"2026年5月21日 – 7月25日","description":"瑞士藝術家尼古拉斯·帕蒂於澤維爾·胡夫肯斯畫廊St-Georges空間展出個展「蜘蛛網」，以粉彩媒材描繪夢幻人物與靜物聞名，以柔和的色彩構建充滿神秘氛圍的超現實場景，以「蜘蛛網」隱喻繪畫媒材本身的脆弱與韌性。","url":"https://www.xavierhufkens.com/"},{"gallery":"Dittrich & Schlechtriem","location":"柏林","region":"歐洲","artist":"Monty Richthofen","title":"HARD 2 4GET","dates":"2026年5月1日起","description":"柏林藝術家蒙蒂·里希特霍芬為柏林畫廊週末創作城市干預計劃，以噴塗標記的車隊穿越柏林市區，將城市街道轉化為表演與文字實驗的舞台，以流動性與轉瞬即逝性重新定義畫廊空間的概念，以社會性身體激活公共空間的生產力。","url":"https://dittrich-schlechtriem.com/"},{"gallery":"Perrotin","location":"洛杉磯","region":"美洲","artist":"Todd Gray","title":"Portals","dates":"2026年3月21日 – 5月30日","description":"美國藝術家托德·格雷於貝浩登洛杉磯空間展出個展「門戶」，以多媒材攝影裝置探索非洲離散經驗、靈性信仰與文化身份認同，結合傳統非洲圖像與當代攝影語言，在視覺「門戶」中開啟關於文化記憶與精神旅程的對話。","url":"https://www.perrotin.com/"},{"gallery":"Perrotin","location":"洛杉磯","region":"美洲","artist":"Kyungmi Shin","title":"My Fantasy's Burdens","dates":"2026年5月1日 – 5月30日","description":"韓裔藝術家申敬美於貝浩登洛杉磯空間展出個展，探索幻想與現實的張力關係。申敬美的繪畫以超現實主義色彩呈現女性內心世界，融合個人敘事與集體記憶，質疑主流文化對女性情感與慾望的規訓，直指幻想所承載的矛盾重量。","url":"https://www.perrotin.com/"},{"gallery":"Gagosian","location":"紐約","region":"美洲","artist":"Anselm Kiefer","title":"Seal My Ears Shut and I Shall Hear You Still","dates":"2026年5月15日 – 6月27日","description":"德國當代藝術巨匠安塞姆·基弗於高古軒紐約展出新作個展。基弗以宏大的歷史題材、神話傳說與詩歌文學為創作資源，結合厚重材質與毀滅性視覺語言，此次展覽標題引用神秘文學意象，延續其對歷史創傷、記憶與救贖的持續追問。","url":"https://gagosian.com/"},{"gallery":"Hauser & Wirth","location":"紐約","region":"美洲","artist":"Firelei Báez","title":"個展","dates":"2026年5月12日 – 7月31日","description":"多明尼加裔美國藝術家費雷萊·貝茲於豪瑟與沃斯紐約舉辦其與畫廊合作的首次個展，呈現全新繪畫、紙上作品及大型青銅雕塑。貝茲的創作深植於加勒比海歷史與神話，以華麗繁複的視覺語言重構被壓抑的歷史記憶。","url":"https://www.hauserwirth.com/"},{"gallery":"David Zwirner","location":"紐約","region":"美洲","artist":"Gerhard Richter","title":"Landschaften","dates":"2026年5月7日 – 7月10日","description":"德國當代藝術大師格哈德·里希特於卓納畫廊紐約展出「風景」系列重要展覽。里希特以模糊攝影的繪畫語言和抽象色彩實驗聞名，此次展覽聚焦其風景繪畫，探索自然景觀的再現與抽象之間的辯證張力，以及繪畫媒介本身的認識論問題。","url":"https://www.davidzwirner.com/"},{"gallery":"David Zwirner","location":"紐約","region":"美洲","artist":"Jasper Johns","title":"Copy/Trace","dates":"2026年5月7日 – 6月26日","description":"美國藝術大師賈斯培·瓊斯於卓納畫廊紐約展出「複製/描摹」個展。瓊斯以旗幟、靶心等日常符號奠定美國新達達與普普藝術的基礎，此次展覽聚焦其「複製」與「描摹」的方法論，探索原作與摹本之間的意義轉化與視覺認知機制。","url":"https://www.davidzwirner.com/"},{"gallery":"White Cube","location":"紐約","region":"美洲","artist":"David Hammons & Jannis Kounellis","title":"David Hammons and Jannis Kounellis","dates":"2026年5月1日 – 6月13日","description":"白立方紐約空間呈現美國觀念藝術家大衛·哈蒙斯與已故義大利藝術家雅尼斯·庫奈利斯的雙人展，兩位藝術家均以貧窮藝術精神著稱，以日常廢棄材料挑戰藝術建制，展覽探索其創作觀念的深層共鳴與跨文化的藝術對話。","url":"https://www.whitecube.com/"},{"gallery":"Marian Goodman Gallery","location":"紐約","region":"美洲","artist":"Julie Mehretu","title":"Our Days, Like a Shadow (a Non-abiding Hauntology)","dates":"2026年4月14日 – 6月6日","description":"埃塞俄比亞裔美國藝術家茱莉·梅荷圖於馬里安·古德曼畫廊紐約展出重要個展。梅荷圖以其複雜的多層次抽象繪畫聞名，疊合建築圖紙、地圖與新聞影像，展覽標題引用幽靈理論，探索歷史暴力在當代的持續縈繞。","url":"https://www.mariangoodman.com/"},{"gallery":"Almine Rech","location":"紐約","region":"美洲","artist":"Alejandro Cardenas","title":"ARACHNE","dates":"2026年5月8日 – 6月13日","description":"智利藝術家亞歷杭德羅·卡德納斯於艾敏·雷克紐約空間展出個展「阿拉克涅」，以希臘神話中被雅典娜變為蜘蛛的織女為主題，探索藝術創作中技藝、創造力與神性懲罰的神話敘事，以細膩的具象繪畫呈現神話世界的當代回響。","url":"https://www.alminerech.com/"},{"gallery":"Almine Rech","location":"紐約","region":"美洲","artist":"Vaughn Spann","title":"(All) Americans","dates":"2026年5月8日 – 6月13日","description":"美國藝術家沃恩·斯潘於艾敏·雷克紐約空間展出個展，探索美國身份認同的複雜面向。斯潘以鮮豔的色彩與充滿活力的抽象語言描繪非裔美國人的日常生活，以藝術行動重新定義「美國性」的多元文化內涵。","url":"https://www.alminerech.com/"},{"gallery":"Regen Projects","location":"洛杉磯","region":"美洲","artist":"Rachel Harrison, Liz Larner, Rebecca Morris","title":"planchette","dates":"2026年4月25日 – 5月23日","description":"里根項目畫廊洛杉磯空間呈現雕塑家瑞秋·哈里森、麗茲·拉納與抽象畫家瑞貝卡·莫里斯三人的首次合展，探索她們在概念主義影響下對抽象語言的各異詮釋，三位長期平行耕耘當代抽象領域的重要女性藝術家首次同台對話。","url":"https://www.regenprojects.com/"},{"gallery":"David Kordansky Gallery","location":"洛杉磯","region":"美洲","artist":"Hilary Pecis","title":"Love Letters","dates":"2026年5月16日 – 6月20日","description":"美國藝術家希拉里·佩西斯於大衛·科丹斯基畫廊展出個展「情書」，以溫暖鮮豔的色彩描繪藝術家工作室、書架與日常生活靜物，洋溢著對創作環境與智識生活的深情頌讚，呈現對藝術家社群與文化生活場域的詩意捕捉。","url":"https://davidkordanskygallery.com/"},{"gallery":"David Kordansky Gallery","location":"洛杉磯","region":"美洲","artist":"Evan Holloway","title":"ROYGBIV","dates":"2026年5月16日 – 6月20日","description":"美國雕塑家埃文·霍洛威於大衛·科丹斯基畫廊展出個展，以彩虹色譜縮寫「ROYGBIV」為題，以機智幽默的雕塑裝置善用日常材料與色彩實驗探索視覺感知的邊界，以色彩光譜為切入點展開對感官認知的哲學探索。","url":"https://davidkordanskygallery.com/"},{"gallery":"Petzel Gallery","location":"紐約","region":"美洲","artist":"Emma Webster","title":"Rues and Leaves Themselves Alone","dates":"2026年4月30日 – 6月6日","description":"美國藝術家艾瑪·韋伯斯特於彼得則爾畫廊展出個展，以數位行走虛擬景觀為核心，從藝術家工作室的立體模型中汲取靈感，以繪畫再現數位遊蕩的風景體驗，探索虛擬與真實之間風景感知的哲學問題。","url":"https://www.petzel.com/"},{"gallery":"Anton Kern Gallery","location":"紐約","region":"美洲","artist":"Lin May Saeed","title":"個展","dates":"2026年5月12日 – 7月2日","description":"德國藝術家林·梅·賽義德於安東·科恩畫廊紐約展出個展，以對動物解放、生態倫理與非人中心主義的深切關懷著稱，以雕塑、繪畫與裝置媒材構建想象中的動物共存烏托邦，以藝術實踐介入環境倫理辯論。","url":"https://antonkerngallery.com/"},{"gallery":"Anton Kern Gallery","location":"紐約","region":"美洲","artist":"Nobuyoshi Araki & Roe Ethridge","title":"攝影展","dates":"2026年5月12日 – 7月2日","description":"安東·科恩畫廊呈現日本攝影大師荒木經惟與美國攝影師羅·艾特里奇的雙人攝影展，由艾特里奇從荒木龐大的檔案中選取並排序，並置兩人系列作品展開跨文化的影像對話，探索攝影在親密性、慾望與死亡主題上的不同文化詮釋。","url":"https://antonkerngallery.com/"}];

let currentRegion = '全部';

function buildCards() {
  ['亞洲','歐洲','美洲'].forEach(region => {
    const grid = document.getElementById('grid-' + region);
    const items = exhibitions.filter(e => e.region === region);
    grid.innerHTML = items.map(e => `
      <div class="card" data-region="${e.region}"
           data-text="${(e.gallery + e.artist + e.title + e.location + e.description).toLowerCase()}">
        <div class="card-top">
          <span class="gallery-name">${e.gallery}</span>
          <span class="location-tag">${e.location}</span>
        </div>
        <div class="artist-name">${e.artist}</div>
        <div class="exhibition-title">${e.title}</div>
        <div class="dates">${e.dates}</div>
        <div class="description">${e.description}</div>
        <div class="card-footer">
          <a href="${e.url}" target="_blank" rel="noopener">畫廊官網</a>
        </div>
      </div>
    `).join('');
  });
  updateCount();
}

function setRegion(region) {
  currentRegion = region;
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.classList.toggle('active', btn.textContent === region);
  });
  filterCards();
}

function filterCards() {
  const q = document.getElementById('search').value.toLowerCase().trim();
  let total = 0;

  document.querySelectorAll('.region-section').forEach(section => {
    const region = section.dataset.region;
    const cards = section.querySelectorAll('.card');
    let visible = 0;

    cards.forEach(card => {
      const matchRegion = currentRegion === '全部' || card.dataset.region === currentRegion;
      const matchSearch = !q || card.dataset.text.includes(q);
      const show = matchRegion && matchSearch;
      card.classList.toggle('hidden', !show);
      if (show) visible++;
    });

    section.classList.toggle('empty', visible === 0);
    total += visible;
  });

  document.getElementById('count').textContent = `顯示 ${total} 個展覽`;
}

function updateCount() {
  document.getElementById('count').textContent = `顯示 ${exhibitions.length} 個展覽`;
}

buildCards();
</script>
</body>
</html>
