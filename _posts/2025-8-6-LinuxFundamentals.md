---

title: "Linux Fundamentals — Arabic HackThe Box ACADEMY Walkthrough"
date: 2025-08-6
author: <author_id>
layout: post
categories: Hack_The_Box_Academy
tags: [Bug_Bounty_Hunter, PenetrationTesting, Security, Hacker]
description: لينكس، النظام المفضل للمخترقين، خلينا نتعرف عليه وناخد اول خطوة بعالم الاختراق
image:
  path: /images/HTB/LinuxFund/0.webp
  alt: 
---

<style>
    h1, h2, h3, h4, h5, h6, p, li {
        font-family: "Tajawal", "Amiri", "Cairo", sans-serif;
    }

    .note {
        background-color: #dff9fb;
        border-right: 5px solid #22a6b3;
        padding: 10px;
        margin: 20px 0;
        border-radius: 5px;
    }

    .warning {
        background-color: #f9e79f;
        border-right: 5px solid #f39c12;
        padding: 10px;
        margin: 20px 0;
        border-radius: 5px;
    }

    .code-title {
        background-color: #2c3e50;
        color: #ecf0f1;
        font-weight: bold;
        padding: 5px 10px;
        border-top-left-radius: 5px;
        border-top-right-radius: 5px;
    }

    .image-box {
        text-align: center;
        margin: 20px 0;
    }

    .image-box img {
        max-width: 80%;
        border: 2px solid #ccc;
        border-radius: 10px;
    }
      .htblogo {
        text-align: center;
        margin: 20px 0;
    }

      .htblogo img {
        width: 100%;
        max-width: 100%;
        border: 2px solid #ccc;
        border-radius: 10px;
    }

  .note {
    background-color: #1e1e1e; /* لون خلفية غامق مريح */
    color: #c9d1d9; /* لون نص فاتح */
    border-left: 4px solid #2ea043; /* شريط أخضر مثل GitHub */
    padding: 12px 16px;
    margin: 20px 0;
    border-radius: 6px;
    font-size: 16px;
    line-height: 1.6;
    box-shadow: 0 2px 5px rgba(0,0,0,0.2);
  }
    .terminal-box {
  background-color:rgb(37, 37, 37); /* نفس الخلفية يلي عندك */
  color: #ccc;
  padding: 1rem;
  border-radius: 6px;
  font-family: monospace;
  font-size: 0.95rem;
  overflow-x: auto;
  border: 1px solid #222;
}

/* ألوان النصوص فقط */
.user   { color: #00afff; }   /* أزرق المستخدم */
.path   { color: #ffaa00; }   /* مسار */
.symbol { color: #00ff00; }   /* $ */
.cmd    { color: #7CFC00; }   /* أمر MySQL */
.input  { color: #ffff66; }   /* إدخال */
.dim    { color: #777; font-style: italic; }  /* رمادي باهت */
.prompt { color: #00ffff; }   /* mysql> */

</style>

<div class="htblogo">
  <img src="{{ '/images/HTB/Untitled.png' | relative_url }}" alt="HTB">
</div>
<a href="https://academy.hackthebox.com/module/details/75" target="_blank" rel="noopener noreferrer" style="font-size:20px">HTB Academy الدرس على</a>

---

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
 مرحبا يا هكرجية👨🏻‍💻، انا فاروق واليوم رح نحكي مقدمة عن تطبيقات الويب ورح نشرح كلشي بال Module من HTB.<br>
 الفكرة انو هالشي عم ياخد وقت وجهد كبير بس انا ماشي على مبدئ زكاة العلم نشره وعسى يكون صدقة جارية لأهلي<br>
 لهيك بس يلي رح اطلبه منك تتذكرنا بدعوة من قلبك وكمان تنشر العلم مع اي حدا مهتم بالمجال وبالتوفيق يارب❤️.<br>
 <strong>إن اخطأت فمن نفسي وإن اصبت فمن الله✨</strong>
</p>

---

<h2 id="Introduction" dir=""><span class="me-2"><strong>Introduction</strong></span><a href="#Introduction" class="anchor text-muted"></a></h2>

<h2 id="📌 Linux Structure:" dir=""><span class="me-2"><strong>📌 Linux Structure:</strong></span><a href="#📌 Linux Structure:" class="anchor text-muted"></a></h2>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  لينكس هو نظام تشغيل مستخدم لأجهزة الكمبيوتر الشخصية والسيرفرات وحتى الموبايلات وهو نفس انظمة التشغيل الثانية، نظام تشغيل لينكس مهم جدا لل Cyber Security وبيشتهر بقوته ومرونته وطبيعته ال 
  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Open Source</span>
  بهالقسم رح نتعرف على اساسيات اللينكس يلي بتهمنا بال
  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Cyber Security</span>.<br><br>
  وبما انو هاد درسنا الأول الفعلي بعالم ال 
  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Cyber Security</span>
  حابب قدملك نصيحة، اي شي بدايته رح تكون صعبة وطويلة ومتعبة والنتائج شبه معدومة بس اتذكر اول مرة جربت تسوق سيارة او حتى تتعلم (قيادة الدراجة🌚) كانت كتير صعبة وكنت خايف من اي خطأ صغير، بس مع الممارسة والصبر والفشل والمحاولة صرت تقدر تسوق باللاوعي تبعك، لهيك اصبر واتعلم واعطلها وقتها حتى توصل لمرحلة تقدر تلاقي الثغرات باللاوعي تبعك😎<br>
  واتذكر دائماً انو مطلوب منك السعي وليس النتيجة.<br><br>
  لينكس هو نظام تشغيل مثل Windows, MacOS, Android ووظيفته انه يسمح لمكونات الجهاز الفيزيائية ال Hardware بطريقة سلسة
</p>

---

<h3 id="🟣 History" dir=""><span class="me-2" style="color:white"><strong>🟣 History</strong></span><a href="#🟣 History" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

حتى نفهم كيف بلش لينكس خلينا نرجع لعام 1970، كان كين طومسون و دينيس ريتشي بيعملوا لصالح شركة AT&T وانشأوا نظام Unix يلي هو الجد الأكبر ل  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Linux</span>.<br><br>
 <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Unix</span> كان متل سيارة فخمة، حلوة ومرتبة بس غالية مو أي شخص بيقدر يشتريها.<br>
وبعام 1977 ظهرت نسخة اسمها  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">BSD</span> بس للأسف شركة AT&T قالوا انو هاد الكود خاص فيهن ومسروق، وصار في دعوات قضائية خربت اهداف  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">BSD</span>.<br><br>
بعام 1983 ريتشارد ستالمان، وهو متل الابطال الخارقين بعالم ال IT، بدأ مشروع اسمه  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">GNU</span> وكان هدفه يساوي نظام تشغيل مجاني شبيه ب  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">UNIX</span> بس كان متل البيت يلي بدون اساس لأنه كان بحاجة  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Kernal</span> قوية (هالشب متلي وانا عم ترجم الدروس مجاناً بدون ما اعرف اذا رح اتقاضى😅)<br><br>

وهون اتدخل لينوس تورفالدس بعام ال 1991 قرر يعمل  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Kernal</span> مجانية كمشروع جانبي شخصي، وفعلاً تم استخدامها لاحقاً لتكون النواة الخاصة بنظام تشغيل لينكس، وهي النواة يلي بلشت بشكل بسيط كمشروع جانبي، اليوم فيها اكتر من 23 مليون سطر برمجي🤯<br><br>
اليوم، لينكس موجود بأكثر من 600 نسخة (توزيعات أو distros)، مثل Ubuntu، Debian، Fedora، وغيرهم. كل توزيعة عبارة عن نكهة مختلفة من الآيسكريم: نفس الأساس، بس الإضافات مختلفة.
</p>

<h3 id="🟣 Philosophy" dir=""><span class="me-2" style="color:white"><strong>🟣 Philosophy</strong></span><a href="#🟣 Philosophy" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
لينكس بحب البساطة والتعاون وفلسفته عبارة عن انه كل اداة تسوي شغلة واحدة بس تسويها بإحترافية. وبعدين بتتجمع هالأدوات لإتمام العمليات المعقدة<br><br>
 كل شي داخل لينكس عبارة عن ملفات، حتى الفلاشة او الطابعة المتصلة بجهازك بتتعرف على انها ملف وبتترتب بطريقة منظمة: <br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Small, single-purpose programs</span>: كل برنامج بيعمل على مهمة وحدة بس بيعملها بإتقان، ورح نتعامل مع كتير برامج ورح نخليها تعمل مع بعضها.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Ability to chain programs together to perform complex tasks</span>: بيسمح انو ناخد نتيجة برنامج وندخلها ببرنامج ثاني، يعني في تكامل كبير بين البرامج.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Avoid captive user interfaces</span>: التركيز بلينكس على استخدام ال Terminal لانه بيعطي مرونة وتحكم اكبر بالأجهزة.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Configuration data stored in a text file</span>: كل البيانات في ملفات نصية حتى إعدادات النظام موجودة في ملفات نصية، مثل ملف /etc/passwd اللي فيه أسماء المستخدمين.<br>
</p>

---

<h3 id="🟣 Components" dir=""><span class="me-2" style="color:white"><strong>🟣 Components</strong></span><a href="#🟣 Componentsphy" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

لينكس بيتألف من عدة عناصر وكل عنصر عنده دور محدد:<br><br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Bootloader</strong></span>: متل البواب يلي بيفتحلك باب النظام وهي بتعمل تمهيد لتشغيل النظام.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>OS Kernel</strong></span>: القلب تبع لينكس، وهي المسؤولة عن إدارة الموارد مثل الذاكرة والمعالج.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Daemons</strong></span>: برامج صغيرة بتشتغل بالخلفية تبع النظام وهي مسؤولة عن انها تتأكد من انه الوظائف الاساسية تعمل بشكل صحيح.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>OS Shell</strong></span>: الشاشة السوداء تبع الهاكر😂، وهي واجهتك مع النظام، مثل لوحة تحكم تكتب فيها الأوامر يلي بدك ياها والنظام ينفذ واشهر shell عنا هي ال <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Bash</span>.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Graphics server</strong></span>: اسمه X-Server، وهو اللي يخلي البرامج الرسومية تشتغل، سواء على جهازك أو عن بُعد.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Window Manager</strong></span>: الواجهة الرسومية مثل GNOME أو KDE، اللي تخليك تفتح متصفح أو ملفات بسهولة.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Utilities</strong></span>: برامج صغيرة تساعدك تسوي مهام معينة، مثل تحرير النصوص أو إدارة الملفات.<br>
</p>

---

<h3 id="🟣 Linux Architecture" dir=""><span class="me-2" style="color:white"><strong>🟣 Linux Architecture</strong></span><a href="#🟣 Linux Architecture" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

منقدر نعتبر لينكس متل مبنى مؤلف من اكتر من طابق وكل طابق عنده وظيفة معينة.<br><br>

- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Hardware</strong></span>: الحديد اللي جوا الجهاز مثل المعالج والرام والقرص الصلب وكل القطع الملموسة بالجهاز.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Kernel</strong></span>: اللي تدير الهاردوير وتعطي كل برنامج الموارد اللي يحتاجها.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Shell</strong></span>: واجهة الأوامر اللي تتكلم فيها مع النواة.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>System Utility</strong></span>: البرامج اللي تساعدك تستخدم النظام بسهولة.<br>
</p>

---

<h3 id="🟣 File System Hierarchy" dir=""><span class="me-2" style="color:white"><strong>🟣 File System Hierarchy</strong></span><a href="#🟣 File System Hierarchy" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
لينكس زي مكتبة كبيرة، كل شيء عنده مكان محدد. الهيكلية تبدأ من المجلد الرئيسي / (الجذر)، وتحته مجلدات فرعية، كل واحد عنده وظيفة
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/LinuxFund/1.png' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/bin</strong></span>: هنا تلاقي الأوامر الأساسية مثل ls وcat. مثل أدواتك اليومية.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/boot</strong></span>: فيه الملفات اللي تحتاجها عشان تشغل النظام، مثل البوتلودر والنواة.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/dev</strong></span>: هنا ملفات الأجهزة. لو عندك فلاش USB، بتلاقي ملفه هنا.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/etc</strong></span>: ملفات الإعدادات. مثلاً، ملف /etc/passwd فيه بيانات المستخدمين.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/home</strong></span>: كل مستخدم عنده مجلد خاص هنا، مثل غرفتك الخاصة.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/lib</strong></span>: لمكتبات اللي تحتاجها البرامج عشان تشتغل.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/media</strong></span>: هنا يتركب الفلاشات أو الأقراص الخارجية.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/mnt</strong></span>: نقطة تركيب مؤقتة للملفات.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/opt</strong></span>: مكان للبرامج الإضافية اللي تضيفها بنفسك.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/root</strong></span>: المجلد الخاص بالمستخدم الرئيسي (root).<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/sbin</strong></span>:  أوامر لإدارة النظام، زي reboot.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/tmp</strong></span>: مكان الملفات المؤقتة، يتمسح غالباً لما تعيد تشغيل الجهاز.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/usr</strong></span>: فيه برامج ومكتبات إضافية.<br>
- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>/var</strong></span>: ملفات متغيرة زي السجلات (logs) أو رسايل الإيميل.<br>


</p>

<script src="https://giscus.app/client.js"
        data-repo="Farouk9423/farouk9423.github.io"
        data-repo-id="R_kgDOONQTbg"
        data-category="General"
        data-category-id="DIC_kwDOONQTbs4CqhWL"
        data-mapping="pathname"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="bottom"
        data-theme="preferred_color_scheme"
        data-lang="ar"
        crossorigin="anonymous"
        async>
</script>
