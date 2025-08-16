---

title: "Introduction to Web Applications — Arabic HackThe Box ACADEMY Walkthrough"
date: 2025-05-19
author: <author_id>
layout: post
categories: Hack_The_Box_Academy
tags: [Bug_Bounty_Hunter, PenetrationTesting, Security, Hacker]
description: بهالدرس رح نحكي عن تطبيقات الويب وكيف بتشتغل ورح نشوفها من وجهة نظر امن المعلومات، لهيك جهز قهوتك ويلا نبلش
image:
  path: /images/HTB/IntroToWebApplications/0.webp
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
<h2 id="Introduction to Web Applications" dir=""><span class="me-2"><strong>Introduction to Web Applications</strong></span><a href="#Introduction to Web Applications" class="anchor text-muted"></a></h2>

<h2 id="📌 Introduction:" dir=""><span class="me-2"><strong>📌 Introduction:</strong></span><a href="#📌 Introduction:" class="anchor text-muted"></a></h2>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  ال Web Application هي عبارة عن برامج بتشتغل داخل المتصفحات متل Firefox,Chrome وبتعتمد على شي اسمو  client-server architecture.<br><br>
  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">العميل (Client):</span> هو المتصفح يلي المستخدم بشوف فيه واجهة التطبيق (Front-end) متل التصميم ولون الأزرار وشكل الصفحة...<br><br>
  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">الخادم (Server):</span> هو جزء ال Back-end، موجود فيه الكود تبع التطبيق وقواعد البيانات.<br>
  الترتيب هاد بخلي الشركات بتقدر تستضيف تطبيقات قوية تتحكم فيها بشكل مباشر وتكون متاحة للناس بكل العالم، متل خدمات البريد من Google، المتاجر الالكترونية متل Amazon، برامج تحرير النصوص متل Google docs<br>
  وهالشي مو مقتصر عالشركات الكبيرة فقط لانو اي Web Developer بيقدر يعمل Web Application ويستضيفه عبر خدمات الاستضافة العادية، وهاد السبب انو في ملايين الWeb Applications ومليارات المستخدمين.
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/1.jpg' | relative_url }}" alt="HTB">
</div>


---
<h3 id="🔵 Web Applications vs. Websites" dir=""><span class="me-2" style="color:white"><strong>🔵 Web Applications vs. Websites</strong></span><a href="#🔵 Web Applications vs. Websites" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
سابقاً، كانت المواقع مملة وجامدة (static)، يعني محتواها ثابت وحتى يتغير لازم المبرمج يدخل عالكود ويضيف عليه يدويا.<br>
يعني مثلا عنا موقع بيعرض معلومات شركة، فهي المعلومات رح تضل ثابتة ومابتتغير اذا حاول المستخدم يتفاعل معها، هي المواقع منسميها Web 1.0، وهي متل ماحكينا بتعرض المعلومات كأنك عم تقرأ جريدة ومابتقدر تغير شي حتى تغيره المطبعة.<br>
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/2.png' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
اما اليوم معظم تطبيقات الويب بتستعمل شي اسمو Web 2.0 وهي التطبيقات بتعرض محتوى متغير (Dynamic) وبيتغير حسب تفاعل المستخدمين معه.<br>
يعني مثلا مثلا لما نفتح اليوتيوب ونضغط على اي زر فالمحتوى قدامي بيتغير حسب الزر يلي كبسته.<br>
وكمان من مميزاتها انها بتشتغل على كل انواع الشاشات يعني مابهم اذا بفتح التطبيق من موبايل او لابتوب او PC كلو شغال وكمان بتشتغل على اي نظام تشغيل OS.
</p>
---
<h3 id="🔵 Web Applications vs. Native Operating System Applications" dir=""><span class="me-2" style="color:white"><strong>🔵 Web Applications vs. Native Operating System Applications</strong></span><a href="#🔵 Web Applications vs. Native Operating System Applications" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
<span style="color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Native OS Applications</span>
هي البرامج يلي بتتثبت على جهازك، متل برامج مايكروسوفت او الألعاب يلي بتشتغل عالويندوز أو الماك. اما ال
<span style="color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Web Applications</span>
فهي مختلفة شوي وعندها اكتر من ميزة.<br><br>
ال Web Application مستقلة عن نظام التشغيل، يعني بتشتغل على اي نظام تشغيل بغض النظر عن نوعه (ويندوز,ماك او حتى لينكس)<br>
وكمان مافي داعي ثبت ال Web Application على جهازي، لأنها بتشتغل على Server بعيد، لهيك مافي داعي خزن مساحة على الهارد تبع المستخدم.<br><br>
وبالإضافة لهالأمور بال Web Application الإصدار موحد للكل، يعني كل المستخدمين عندهم نفس نسخة الإصدار للتطبيق، وبتم تحديثه على ال Server بدون الحاجة للإرسال تحديثات للمستخدم. وهالشي بقلل تكاليف الصيانة والدعم.<br><br>
بس كمان ال Native OS Applications في الها إيجابيات متل انها اسرع لأنها بتستخدم ملفات ومكتبات موجودة عالنظام والأجهزة المحلية، وكمان عندها قدرات افضل لانها بتستخدم موارد الجهاز بشكل اعمق بكتير مقارنة بتطبيقات الويب يلي بتعتمد على امكانيات المتصفح.<br><br>
آخر كم سنة طلع عندي شي اسمه
<span style="color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Hybrid and Progressive Web Apps</span>
وهاد عبارة عن دمج لمميزات التنين فهي بتستخدم أطر عمل حديثة وبتعمل بسرعة اكبر وبتستفيد من موارد الجهاز.
</p>


<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
في لل Web Applications نوعين رئيسيين:<br>
<span style="color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">مفتوحة المصدر (Open Source)</span>:
اي شخص ممكن يدخل عالكود تبعها ويعدل عليها لتلبي احتياجه، وهي يلي بتفضله الشركات لانها بتقدر تعدل عليها حسب شو بناسبها، امثلة عنها:
</p>
- WordPress: لإنشاء المواقع والمدونات
- OpenCart: لإنشاء المتاجر الإلكترونية
- Joomla: لإدارة المحتوى
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
<span style="color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">مغلقة المصدر (Closed Source)</span>:
وهي يلي بتطورها الشركات وبتبيعها، او بتسمح باستخدامها بإشتراك، متل:
</p>
- Wix: لإنشاء المواقع
- Shopify: لإنشاء متاجر إلكترونية
- DotNetNuke: لإدارة المحتوى

---

<h3 id="🔵 Security Risks of Web Applications" dir=""><span class="me-2" style="color:white"><strong>🔵 Security Risks of Web Applications</strong></span><a href="#🔵 Security Risks of Web Applications" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
بما انو ال Web Applications ممكن الوصول اليها من اي مكان بالعالم بمجرد مايكون عندك اتصال بالانترنت فهالشي سمح لأي شخص لأي شخص انو يقدر يهجم عليها، وكل ما كان ال Web Application اكبر ومعقد اكتر كل ما زاد احتمال انو يكون عندي فيها مشاكل امنية، وخاصة انو عندي أدوات تلقائية لمسح وفحص ومهاجمة ال Web Applications، ولما الهاكر يستخدم هالأدوات رح يسببلي مشاكل ومخاطر كبيرة.<br><br>
اذا فرضا الهاكر قدر يخترق ال Web Application بسبب خسائر مالية وبتتوقف الأعمال وممكن يصير تسريب لبيانات حساسة متل معلومات العملاء والشركات، لأنه غالبا ال Web Applications بترتبط ب Servers وبقواعد بيانات بتحتوي على هدول المعلومات.<br><br>
لهيك ضروري عالشركات انو تختبر تطبيقاتها مشان تكتشف الثغرات وتحاول إصلاحها بسرعة قبل ما الهكر يكتشفها🌚، ولازم تعتمد على مبدئ ال Secure Coding، واكيد لازم تتأكد انو اصلاح الثغرات ما يفتح ثغرات جديدة(يعني بالله شو استفدنا لم نصلح ثغرة بس نفتح وحدة غيرها😂🤦‍♂️)<br><br>
بالنسبة لاخبار اختراق ال Web Applications، اسمها Web Application Penetration Testing، وهي مهارة لازم الشخص يلي بدو يشتغل بالمجال يكون بيعرف كيف بيشتغل ال Web Application بالأصل لأنو مافيك تخترق شي مابتعرف كيف بيشتغل🌚، ولازم نتعلم كيف بتم تطوير ال Web Applications وشو هي المخاطر الخاصة بكل طبقة وبكل مكون من مكونات التطبيق حسب شو التقنيات المستخدمة.<br><br>
وحدة من الطرق المستخدمة كتير هي استخدام دليل OWASP، وهو مرجع عالمي بال Web Penetration Testing.<br><br>
وحدة من الإجراءات المشهورة هي انو نبلش بالتأكد من امان ال Front end ونراجع كود ال HTML, CSS, Java Script وهنن اللغات المشهورة يلي بتم من خلالهم بناء ال Web Applications، فمنتأكد انو الكود مكتوب بطريقة Secure ومنحاول ندور على نقاط ضعف متل Sensitive Data Exposure وهي مهاجمة البيانات الحساسة لل Web Application وبسبب اختراق لكل البيانات يلي لازم تنحمى، وال  Cross-Site Scripting (XSS) بتسبب انو المهاجم بيقدر يوصل برامج خبيثة لل Web Application أو سرقة ال Sessions.<br><br>
ولايهمك اذا مافهمت كتير، رح نحكي عنهن بالتفصيل لقدام لساتنا بالمقدمة حاليا🫠<br><br>
بعد ما نراجع كل المكونات الاساسية بال Front end منرجع ومنتأكد من باقي الوظائف الخاصة بال Web Applicatoin واتصاله بالسيرفرات وبدور عالمشاكل او الثغرات بالسيرفر.<br>
وعادةً منقيم ال Web Application كشخص خارجي وكشخص داخلي، يعني مثلا عندي موقع بيتطلب تسجيل دخول، بشوف النتائج مرة بدون ما يكون عندي حساب ومرة وانا عندي حساب مشان اعمل مراجعة لكل السيناريوهات المحتملة عندي.
</p>
---
<h3 id="🔵 Attacking Web Applications" dir=""><span class="me-2" style="color:white"><strong>🔵 Attacking Web Applications</strong></span><a href="#🔵 Attacking Web Applications" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
معظم الشركات بغض النظر عن حجمها عندها Web Applicatoin خاص فيها، بدايةً من الشغلات البسيطة متل ال Static وصولا لمدونات كبيرة بتشتغل بأنظمة إدارة المحتوى متل WordPress, وصولا لانظمة كبيرة فيها تسجيل دخول وادوار للمستخدمين (متل مستخدم عادي وادمن و...)<br>
وبسبب طبيعتها ال Dynamic بتتغير هالتطبيقات باستمرار، واي تغيير بسيط ممكن يودي لظهور ثغرات خطيرة.<br><br>
موجود العديد من الثغرات الخطيرة يلي ممكن تطلع عندي، وحدة منهن هي ال
<span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">SQL Injection</span>
بتصير لما حدا يتعامل مع طلبات المستخدم بشكل غير آمن، وهالشي بيسمح للمهاجم بالوصول لقاعدة البيانات وقراءة الملفات او حتى تنفيذ اوامر على السيرفر.
</p>
<div class="note" dir="rtl" style=" font-size: 20px;">
    <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">✅ ملاحظة: </span>
حكينا عن ال SQL Injection بدرس تاني بالتفصيل بتقدر ترجع تشوفها وهي اللينك تبعها 
<a href="https://farouk9423.github.io/posts/SQLfundemantle/" target="_blank" rel="noopener noreferrer" style="font-size:20px">SQL Injectoin</a>
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
<br>
الثغرة يلي بعدها هي
<span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">File Inclusion</span>
وهي بتسمح للمهاجم بقراءة Source Code (الكود تبع التطبيق) حتى اوصل لصفحات او لملفات مخفية وهيك بقدر اكشف وظائف مخفية مو مصرح الي اني اوصلها وممكن تؤدي لتنفيذ أوامر عن بعد.<br><br>
بعدين بيجي عنا ال <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Unrestricted File Upload</span>
وهي لما بيسمح التطبيق برفع الملفات بدون تحقق (مثل لما يكون التطبيق بيسمح الي اني ارفع صورة فبرفع برنامج ضار بدلاً من صورة)، وهيك ممكن للمهاجم السيطرة على ال server.<br><br>
وبعدين بيجي عنا ال
<span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Insecure Direct Object Referencing (IDOR)</span>
وهي لما بيقدر المستخدم انو يوصل لبيانات أو وظائف بتخص مستخدمين آخرين.<br> على سبيل المثال، إذا كان في رابط لتعديل ملفك الشخصي مثل<br> /user/701/edit-profile، يمكن للمهاجم تغيير الرقم إلى 702 لتعديل ملف مستخدم آخر.<br><br>
آخر الشي عنا ال
<span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Broken Access Control</span>
النظام عندي هو المسؤول عن تحديد الصلاحيات للمستخدمين، بس لما يصير عندي خطأ بالتنفيذ المهاجم ممكن يستغل هالشي ويوصل لمكان مو مسمحله يوصله.<br><br>
مثلاً عندي موقع بيسمح لأي شخص يعمل حساب جديد وبيطلب منه اسم المستخدم وكلمة السر والإيميل بس المشكلة انو بيبعت كمان rolied وهاد رقم بمثل صلاحية الحساب يعني مثلا rolied=3 يعني الحساب لمستخدم عادي، اما اذا كانت rolied=1 فالمستخدم ادمن، واذا كانت rolied=0 بكون صاحب النظام وهاد اعلى من الأدمن.<br>
واي حدا بدو يعمل حساب جديد الموقع بيرسل عالسيرفر هاد الطلب
</p>
```
POST /register
username=bjones&password=Welcome1&email=bjones@domain.com&roleid=3
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
فهون المهاجم صار يفكر ليش ما غير ال rolied=3 ل rolied=1?<br>
وصار عندي الطلب هيك:
</p>
```
POST /register
username=hacker&password=123456&email=hacker@evil.com&roleid=1
```

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
والمفاجأة؟ 😏<br>
إذا ما كان في تحقق منيح بالسيرفر، الموقع رح يسجل الحساب كـ ادمن مباشرة!!<br>
الموقع عطاك صلاحيات مو من حقك بس لأنك غشيت برقم صغير، وهالشي بسبب إنو مافي تحقق حقيقي من السيرفر على صلاحية المستخدم.
</P>
---

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
<span style=" color:rgb(221, 39, 78); font-size: 27px; line-height: 1.6;"><strong>مثال واقعي:</strong></span><br>
اذا كان عندي تطبيق ويب بيستخدم شي اسمه Active Directory لتسجيل الدخول للمستخدمين، ممكن لثغرة ال SQL Injection انو تسمح للهاكر باستخراج ايميلات المستخدمين وبقدر استخدم هالايميلات بهجوم Password Spraying (بحاول بكلمات السر المشهورة على كتير حسابات) ضد بوابات ال VPN او حتى الايميلات وهالشي بيسمحلي اوصل للبيانات الحساسة او حتى اني اخترق الشبكة الداخلية للشركة.
</p>
---
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
لا تخاف اذا حسيت اي شي من الحكي يلي حكيناه صعب، لانو رح نحكي عليهن لقدام بالتفصيل إن كان بهاد الدرس او بالدروس القادمة، ورح تصير تلاقيهن شوربة (شوربة = بغاية السهولة😂)<br>
<strong>لهيك يلا يا بطل خلينا نكمل وما نوقف هون وتذكر انو لازم تحس حالك غبي انت وعم تدرس حتى تصير عبقري🔥...</strong>
</p>
---

<h2 id="📌 Web Application Layout:" dir=""><span class="me-2"><strong>📌 Web Application Layout:</strong></span><a href="#📌 Web Application Layout:" class="anchor text-muted"></a></h2>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  كل Web Application موجود مختلف عن التاني، لأن كل شركة بتبني التطبيق الخاص فيها بناءً على احتياجاتها والجمهور يلي بتستهدفه، لهالسبب تطبيقات الويب بتختلف بطريقة برمجتها وتصميمها والبنية التحتية متل السيرفرات والأنظمة يلي بتدعمها.<br><br>
  ولنفهم تطبيق الويب لازم نعرف 3 اشياء رئيسية:<br>
  1- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">البنية التحتية (Infrastructure)</span>:
  يعني الأجهزة والسيرفرات يلي بتشغل التطبيق، متل قاعدة البيانات (Database) أو السيرفر المستضيف لل Web Application.<br><br>
  2- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">مكونات التطبيق (Components)</span>:
  وبتتألف من الأجزاء يلي بيتكون منها التطبيق، متل واجهة المستخدم(Frontend) والمكونات يلي بيتفاعل معها.<br><br>
  3- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">هندسة التطبيق (Architecture)</span>:
  عبارة عن العلاقة بين كل هالمكونات مع بعضها وكيف بتتفاعل مع بعض.
</p>
---
<h3 id="🟢 Web Application Infrastructure" dir=""><span class="me-2" style="color:white"><strong>🟢 Web Application Infrastructure</strong></span><a href="#🟢 Web Application Infrastructure" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  البنية التحتية هي متل حجر الأساس يلي بقوم عليه ال Web Application، متل ماحكينا تطبيقات الويب بحاجة سيرفرات وقواعد بيانات عشان تشتغل، وفي أربع طرق رئيسية لبناء هالعملية:<br><br>
</p>

- Client-Server
- One Server
- Many Servers - One Database
- Many Servers - Many Databases

---

<p>
<strong style="color:white; font-size:20px">Client-Server</strong>
</p>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  هاد اشهر Model، واغلب تطبيقات الويب بتستخدمه
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/3.jpg' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  الفكرة من هال Model انو بكون عندي Server (جهاز كمبيوتر قوي)، والمستخدمين بيدخلو لهالسيرفر من خلال متصفح الانترنت على اجهزتهم (كمبيوتر او موبايل...)<br><br>
  وهاد ال Model بقسم التطبيق لجزئين:<br>
  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Front-End</span>:
  وهو عبارة عن الشي يلي بتشوفه بالمتصفح، متل الأزرار والنصوص وهاد الجزء بيتنفذ على المتصفح بجهازك.<br><br>

  <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Back-End</span>:
  هون السيرفر هو يلي بيتعامل مع الطلبات، متل تسجيل الدخول او إضافة منتج على عربة التسوق مثلاً، السيرفر بياخد طلبك وبعالجه وبعدين برد عليك بالنتيجة.<br><br>
  <span style=" color:rgb(221, 39, 78); font-size: 27px; line-height: 1.6;"><strong>مثال واقعي:</strong></span><br>
  لما العميل يزور عنوان URL ل Web Application ولنفرض مثلا انه <a href="https://www.facebook.com/">Facebook.com</a> بيستخدم السيرفر واجهة التطبيق الرئيسية UI.<br><br>
  ولما المستخدم يضغط على زر او يطلب وظيفة معينة، بيرسل الويب HTTP Request للسيرفر، والسيرفر بفسر هالطلب وبنفذ المهام اللازمة لإكمال الطلب.<br><br>
  يعني اذا فتت عالفيسبوك وكتبت ايميلك وكلمة السر وضغطت على Login، الويب بيرسل ال HTTP Request للسيرفر وبقوم السيرفر بمطابقة الايميل وكلمة السر مع قاعدة البيانات يلي عنده وبعدها بيرجع بأرسل HTTP Response للمتصفح الخاص فيك وبقوم بتحويلها للغة مقروءة وبيعرضلك صفحتك الشخصية.
</p>

---

<p>
<strong style="color:white; font-size:20px">One Server</strong>
</p>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  هون كلشي (التطبيق وقاعدة البيانات  وكلشي) موجود على سيرفر واحد وهاد model بسيط وسهل تنفيذه بس خطير!<br>
  ليش؟ لأنك بتكون حاطت كل البيض تبعك بسلة وحدة وإذا تم اختراق اي تطبيق، فبتكون كل بياناتك معرضة للإختراق، ولو السيرفر وقف عن العمل (وقع) كل التطبيقات بتصير غير متاحة.
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/4.jpg' | relative_url }}" alt="HTB">
</div>

---

<p>
<strong style="color:white; font-size:20px">Many Servers - One Database</strong>
</p>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  هون قاعدة البيانات على سيرفر منفصل، والتطبيقات على سيرفرات تانية.<br>
  يعني لو في أكتر من تطبيق، كلهم يتشاركون نفس قاعدة البيانات.
الميزة هون لو سيرفر واحد اتعرض للاختراق، الباقي ما يتأثر بشكل مباشر.<br>
ولو قاعدة البيانات اتعرضت لمشكلة، التطبيق نفسه ما يتأثر مباشرة،
بس لازم يكون في تحكم صارم بالأشخاص يلي تقدر تدخل على البيانات.
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/5.jpg' | relative_url }}" alt="HTB">
</div>

---

<p>
<strong style="color:white; font-size:20px">Many Servers - Many Databases</strong>
</p>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  هاد أكتر نموذج متقدم. كل تطبيق ويب عنده قاعدة بيانات خاصة فيه، وكل قاعدة بيانات على سيرفر منفصل.<br>
  الميزة عندي أمان عالي جدًا، لأن البيانات مفصولة، ولو في مشكلة بسيرفر أو بقاعدة بيانات، الباقي بيبقى شغال.<br>
  بيستخدموه كتير عشان التكرار (Redundancy)، يعني لو سيرفر وقف، في سيرفر احتياطي بيشتغل بداله.<br>
  بس هاد ال model معقد وبيحتاج أدوات متل "Load Balancers" عشان يوزع الطلبات بين السيرفرات.
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/6.jpg' | relative_url }}" alt="HTB">
</div>

---

<h3 id="🟢 Web Application Components" dir=""><span class="me-2" style="color:white"><strong>🟢 Web Application Components</strong></span><a href="#🟢 Web Application Components" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  ال Web Application بيتكون من اجزاء، بغض النظر عن ال model المستخدم، وهي اهم الأجزاء:<br><br>
  1- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Client</span>:
  وهاد جهازك، الموبايل او الكمبيوتر والمتصفح يلي بيستخدمه<br>
  2- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Server</span>:
  بيتضمن:<br>
    &nbsp;&nbsp;&nbsp;&nbsp;<span style=" color:rgb(38, 201, 190); font-size: 20px; line-height: 1.6;">Web Server</span>: يستضيف التطبيق وبرد على طلباتك.<br>
    &nbsp;&nbsp;&nbsp;&nbsp;<span style=" color:rgb(38, 201, 190); font-size: 20px; line-height: 1.6;">Application Logic</span>: البرمجة يلي بتحدد شو يصير وقت تضغط على زر معين مثلاً (Backend)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;<span style=" color:rgb(38, 201, 190); font-size: 20px; line-height: 1.6;">Database</span>: المكان اللي تتخزن فيه البيانات متل بيانات حسابك.<br>
  3- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Services</span>:
  الخدمات الخارجية(دفع PayPal) أو الخدمات الداخلية بين التطبيقات.<br>
  4- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Functions</span>:
  هي بتطبيقات ال Serverless، يعني التطبيق بيشتغل من غير ما تحتاج تدير السيرفرات بنفسك متل خدمات AWS.
  
</p>

---

<h3 id="🟢 Web Application Architecture" dir=""><span class="me-2" style="color:white"><strong>🟢 Web Application Architecture</strong></span><a href="#🟢 Web Application Architecture" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  نحنا شفنا المكونات او الأجزاء الخاصة بال Web Application، طيب السؤال حالياً، كيف بدو يكون ترتيب هالمكونات يعني اكيد ما رح يكون عشوائي؟ وكيف هالمكونات بتتفاعل مع بعض؟<br><br>
  بالعادة ال Web Application بتنقسم لعدة طبقات:<br>
  1- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">طبقة العرض(Presentation Layer)</span>:
  وهي عبارة عن الواجهة يلي بتشوفها بالمتصفح(HTML, CSS, JavaScript) وهي مسؤولة عن عرض الموقع بشكل مرتب وسهل.<br>
  2- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">طبقة التطبيق(Application Layer)</span>:
  وهالطبقة مسؤولة عن معالجة الطلبات، يعني لما تطلب شي، السيرفر بيتحقق من الصلاحيات وبعالج الطلب.<br>
  3- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">طبقة البيانات (Data Layer)</span>:
  هون بتتخزن البيانات وبتستدعى من قاعدة البيانات عحسب الحاجة.<br><br>
  وهي مثال عن البنية الهندسية لل Web Applicatoin من مايكروسوفت:
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/7.png' | relative_url }}" alt="HTB">
</div>

---

<h3 id="🟢 Microservices" dir=""><span class="me-2" style="color:white"><strong>🟢 Microservices</strong></span><a href="#🟢 Microservices" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
  الميكروسيرفيسز هي متل قطع صغيرة من التطبيق، كل قطعة مسؤولة عن مهمة معينة مثلاً، عنا متجر إلكتروني موجود فيه اكتر من قطعة في قطعة لتسجيل الحسابات، وقطعة للبحث عن المنتجات وقطعة للدفع، وكل قطعة بتكون مستقلة لحالها، بس بتقدر القطع انها تحكي مع بعض.<br>
  والميزة بهالشي إنها مرنة، يعني لو بدي ضيف ميزة جديدة مافي داعي اني غير بالتطبيق كله.
</p>

---

<h3 id="🟢 Serverless" dir=""><span class="me-2" style="color:white"><strong>🟢 Serverless</strong></span><a href="#🟢 Serverless" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
في نموذج حديث اسمه Serverless، يعني ما تحتاج تدير السيرفرات بنفسك.<br> شركات متل Amazon أو Google بتوفر لك بنية جاهزة، والتطبيق يشتغل في بيئة "افتراضية" من غير ما تهتم بصيانة السيرفرات، وهالشي بوفر وقت وجهد.
</p>

---

<h3 id="🟢 Architecture Security" dir=""><span class="me-2" style="color:white"><strong>🟢 Architecture Security</strong></span><a href="#🟢 Architecture Security" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
كتير ضروري انك تفهم البنية العامة لل Web Application وكمان مهم أنك تفهم البنية العامة لكل تطبيق قبل ما تجرب تعمل اختبار اختراق،
لانه كتير اوقات الثغرات ما بتكون عبارة عن خطأ ببرمجة ال Web Application، بس بتكون عبارة عن خطأ بتصميم بنية التطبيق.<br><br>

تخيل عنا تطبيق ويب (موقع تسوق إلكتروني مثلا) وكل الوظائف الأساسية فيه (متل إضافة منتج لعربة التسوق أو تسجيل الدخول) مبرمجة بشكل آمن، يعني مافي أخطاء برمجية واضحة بالكود.<br>
لو التصميم ما بيحتوي على إجراءات تحكم بالوصول (Access Control) بشكل صحيح، ممكن يحصل مشكلة كبيرة، وممكن اي مستخدم عادي يقدر يوصل لصلاحيات الآدمن.<br>
إجراءات تحكم الوصول هي القواعد اللي بتحدد مين يقدر يشوف أو يستخدم إيش في التطبيق.<br><br>

مثال تاني تخيل إنك هاجم على تطبيق واستغليت ثغرة (يعني اخترقت ال Back-End Server). بس لما حاولت تدور على قاعدة البيانات (اللي فيها بيانات المستخدمين متل الأسماء وكلمات المرور)، ما لقيتها! ليه؟ لأن قاعدة البيانات موجودة على سيرفر منفصل مو على نفس السيرفر اللي اخترقته. وهاد مثال على تصميم جيد من ناحية الأمان، لأن فصل قاعدة البيانات عن السيرفر الرئيسي بيقلل من الضرر لو سيرفر واحد اتعرض للاختراق.<br><br>
هاد هو السبب أنه يجب مراعاة الأمان بكل مرحلة من مراحل تطوير تطبيقات الويب ، ويجب عمل اختبارات الاختراق بكل دورة حياة تطوير تطبيقات الويب. 
</p>

---

<h2 id="📌 Front End vs. Back End:" dir=""><span class="me-2"><strong>📌 Front End vs. Back End:</strong></span><a href="#📌 Front End vs. Back End:" class="anchor text-muted"></a></h2>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

اكيد كلنا سمعنا بمبرمج Front end او مبرمج Back end وال Full stack، وهاد البني ادم يلي بيشتغل فرونت وباك😎<br>
كل واحد من هدول المصطلحات بركز على جانب من تطوير ال Web Application، ورح نحكي عن كل وحدة لحال.
</p>

---

<h3 id="🟣 Front End" dir=""><span class="me-2" style="color:white"><strong>🟣 Front End</strong></span><a href="#🟣 Front End" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

  وهي بتكون عبارة عن واجهة التطبيق وهي الجزء يلي بيتفاعل معه المستخدم بشكل مباشر من خلال المتصفح، ومنسميها احياناً ال Client Side، وهاد الجزء بيتكون من الاجزاء يلي منشوفها لما نزور اي تطبيق ويب وبتضمن:<br><br>
  1- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">HTML</span>:
  لغة الترميز يلي بتحدد هيكلية الصفحة، متل عناوين ونصوص وروابط وصور.<br>
  2- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">CSS</span>:
  لتنسيق الصفحات، يعني لتحديد الالوان ونوع الخط المستخدم وتنسيق ال HTML بشكل عام.<br>
  3- <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">JavaScript</span>:
  وهي لغة البرمجة المسؤولة عن انها تضيف التفاعل على الصفحة، متل النوافذ المنبثقة، الأزرار يلي بتستجيب للنقر، أو تحميل البيانات ديناميكيًا، يعني هي العصب تبع الموقع يلي بتخليه قابل للتفاعل ومو جامد متل ماحكينا سابقاً.<br><br>
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/8.jpg' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
وكل هالمكونات يلي بتشكل ال Front end بتتنفذ بالوقت الفعلي بالمتصفح يلي بتستخدمه، وهالشي يعني انو كلشي بتشوفه وبتتفاعل معه على الشاشة هو جزء من ال Front end.<br><br>
مبرمج ال Front end عنده عدة وظائف لازم يطبقها بكل Web Application، بداية من إنشاء العناصر الأساسية متل العناوين (Headings) والنصوص (Text) والصور (Images)، وكمان مسؤول عن التصميم والتنسيق والتحكم بشكل الصفحة وجماليتها باستخدام CSS، وايضا بكون مسؤول عن الوظائف التفاعلية وبحدد وظيفة كل جزء بالصفحة باستخدام JavaScript، متل تحديث محتوى الصفحة بدون إعادة تحميلها.<br><br>
وبسبب هالوظائف في كمان تحديات لمبرمج ال Front end، متل مامنعرف ال Web Applications الجديدة لازم تكون مكونات ال Front end متوافقة مع كل انواع واحجام الشاشات ومع كل انواع المتصفحات والأجهزة (يعني تخيل عندي موقع بيشتغل على ال Chrome بس مابيشتغل على ال Firefox🤦‍♂️)<br>
اذا ال Front end مو مبرمجة بشكل جيد، فهالشي ممكن يسببلي بطئ بالتطبيق وهالشي ممكن يخلي المستخدمين يعتقدوا المشكلة بالServer بس هي بال Client Side.<br><br>
بالإضافة لكل هالأمور عندي لسا وظائف لل Front end (مشان ما تفكر شغلتو سهلة وتقول عنه نقاش🌚)، عنا اول شي تصميم المفهوم (Visual Concept Web Design) يعني إنشاء التصور الأولي لشكل الموقع، ومسؤول كمان عن تصميم واجهة المستخدم (User Interface-UI) وهو تصميم العناصر يلي بيتفاعل معها المستخدم متل الأزرار والقوائم، وآخر الشي تصميم تجربة المستخدم (User Experience-UX) وهي تحسين تجربة المستخدم بحيث تكون سهلة ويكون التطبيق سلس بالأستخدام.
<br><br>
<span style="  color:rgb(221, 39, 78); font-size: 27px; line-height: 1.6;"><strong>مثال عملي:</strong></span><br>
في كتير محررات نصوص على الانترنت ممكن نستخدمها حتى نطبق عملي على الشي يلي تعلمنا متل: 
<a href="https://html-css-js.com/" target="_blank" rel="noopener noreferrer" style="font-size:20px">Editor</a><br>
بتقدر بالبداية تجرب تحط هالكود:
</p>

```html
<p><strong>Welcome to Hack The Box Academy(Hack With Farouk Academy🌚)</strong></p>
<p><em>This is some italic text.</em></p>
<p><span style="color: #0000ff;">This is some blue text.</span></p>
```

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
هاد الكود البسيط بيظهر نص غامق (Bold) باستخدام وسم strong<br> ونص مائل باستخدام وسم em<br>ونص ملون بالأزرق باستخدام خاصية style في ال css <br><br>
لما ندخل هاد االكود بالمحرر منقدر نشوف النتيجة مباشرة، ومنقدر نعدل على التنسيقات (متل تغيير الألوان او إضافة عناوين) وشوف كيف بتتغير الصفحة. 
</p>

---

<h3 id="🟣 Back End" dir=""><span class="me-2" style="color:white"><strong>🟣 Back End</strong></span><a href="#🟣 Back End" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
وهو الجزء بال Web Application يلي بيشتغل على ال Server Side، ومسؤول عن تشغيل كل الوظائف الاساسية للتطبيق وهاد الجزء يلي ما بشوفه المستخدم وما بيتعامل معه بشكل مباشر بس بكون ضروري لتشغيل ال Web Application وبدونه ال Web Application بكون مجرد صفحات ثابتة يلي ما بتحتوي على اي وظائف (حسيته باتمان، مابتشوفه ولا بتتعامل معه بس مابتقدر بلاه😎)
<br><br>
تتألف ال Back end من اربع مكونات اساسية:<br><br>

- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Back End Servers </strong> </span>: 
وهي عبارة الأجهزة المادية وأنظمة التشغيل يلي بتستضيف كل مكونات ال Back end، وبتعتمد غالباً على انظمة تشغيل متل Windows, Linux او باستخدام حاويات (Containers) متل Docker.<br><br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Web Servers </strong></span>: 
مسؤولة عن معالجة طلبات HTTP وعن التوصيلات بين ال Client Side وال Server Side امثلة عنها: Apache، NGINX، وIIS.<br><br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Databases </strong></span>: 
بستخدمها لخزن فيها واسترجع منها بيانات التطبيق، وفي الها نوعين Relational Databases متل MySQL، MSSQL، Oracle، PostgreSQL وال Non-Relational Databases متل MongoDB، NoSQL.<br><br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Development Frameworks </strong></span>: 
بيستخدمها المبرمج لتطوير التطبيق الأساسي متل ال Laravel (PHP)، ASP.NET (C#)، Spring (Java)، Django (Python)، Express (NodeJS JavaScript)..<br><br>

</p>
<div class="note" dir="rtl" style=" font-size: 20px;">
    <span style=" color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">✅ ملاحظة: </span>
طبعا رح يتم شرح كلشي بالتفصيل إن كان بهاد الدرس او بالدروس القادمة بس عم ناخد نظرة عامة عن تطبيقات الويب حالياً.
</div>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/9.jpg' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
ممكن انو نستضيف كل المكونات ال Backend على Server منفصل أو ب Containers معزولة باستخدام تقنيات متل ال Docker، وهاد الفصل بساعد بعزل المكونات بحيث انه تكون قاعدة البيانات بحاوية منفصلة عن التطبيق الرئيسي وهالشي بقلل من تأثير الثغرات الأمنية، وكمان بساعد بتحسين الأمان بحيث إذا انصابت وحدة من الحاويات بثغرة ما بتتأثر باقي الحاويات، وكمان رح تكون اوفر من اني حط كل مكون على Server منفصل.<br><br>
حكينا عن المهام الاساسية لل Front end ورح نحكي هلق عن مهام ال Back end:<br><br>
اول شي بناء الوظائف الاسياسية يلي بتخلي التطبيق يعمل وتطوير الكود المسؤول عن إدارة سلوك التطبيق، وايضا تطوير وصيانة قواعد البيانات، ومسؤولة عن إنشاء المكتبات البرمجية يلي بيستخدمها التطبيق وتنفيذ المتطلبات يلي بيحتاجها التطبيق، وتطوير ال APIs لتسهيل التواصل بين ال Front end وال Back end، ودمج الخدمات السحابية.
</p>

---

<h3 id="🟣 Securing Front/Back End" dir=""><span class="me-2" style="color:white"><strong>🟣 Securing Front/Back End</strong></span><a href="#🟣 Securing Front/Back End" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
صح انو غالبا ما منقدر نوصل للكود المصدري (Source Code) الخاص بال Back end حتى نحلله مباشرة بس تطبيقات الويب ابدا مو محصنة ضد الهجمات على سبيل المثال:<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>هجمات الحقن (Injection Attacks) </strong> </span>: 
متل حقن SQL، الهاكر بيتلاعب باستعلامات قاعدة البيانات حتى يوصل لبيانات من غير المسموح انه يوصلها..<br><br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>هجمات تنفيذ الأوامر (Command Injections) </strong> </span>: 
المهاجم بنفذ أوامر نظام التشغيل من خلال ال Web Application.<br><br>
وعنا نوعين من اختبارات امان التطبيقات، اول شي ال
<span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Whitebox Pentesting</strong> </span>
لما يكون عندي وصول لل Source Code تبع التطبيق وبقدر اعمل Review على الكود تبع التطبيق
النوع التاني هو ال
<span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Blackbox Pentesting</strong> </span>
وهون مابكون عنا وصول لشي ومنعمل الاختبار بدون معرفة التفاصيل الداخلية، ومع هيك، إذا كان التطبيق مفتوح المصدر، أو إذا قدرنا نحصل على الكود عبر ثغرات متل تضمين الملفات المحلية (Local File Inclusion)، منقدر نراجع الكود حتى نعثر على بيانات حساسة (مثل كلمات المرور) أو ثغرات.<br><br>
رح نحكي هلق عن أهم 20 خطأ بيعمله المبرمجين وبسبب ثغرات امنية، رح نحكيهن حالياً بدون شرح ورح نشرحهن اكتر مع الوقت:<br><br>

1- السماح بإدخال بيانات غير صالحة إلى قاعدة البيانات<br>
وهالشي بصير لما المبرمج مابيتحقق من صحة البيانات يلي بدخلها المستخدم (مثل الحقول في نموذج). مثلاً إذا أدخل المستخدم رمز ضار داخل حقل الاسم، هالشي ممكن يتسبب بهجمات مثل حقن SQL.<br><br>

2- التركيز على النظام ككل بدلاً من التفاصيل<br>
بركز بعض المبرمجين على الأداء العام للتطبيق بدون التحقق من أمان كل جزء (مثل التحقق من المدخلات أو تشفير البيانات). هالشي بيترك ثغرات داخل أجزاء صغيرة ممكن انها تُستغل.<br><br>

3- إنشاء طرق أمنية مخصصة غير موثوقة<br>
بدال ما يستخدم مكتبات أمنية موثوقة (مثل مكتبات التشفير القياسية)، بعض المبرمجين بيتذاكوا وبحاولوا يعملو حلول أمنية خاصة فيهم، وهي غالبًا ضعيفة وسهلة الاختراق.<br><br>

4- تأخير الاهتمام بالأمان إلى المرحلة الأخيرة<br>
 بعض المبرمجين بيهملوا الأمان في بداية التطوير وبيتركوه للأخير، وهالشي بخلي إصلاح الثغرات اصعب واغلى.<br><br>

5- تخزين كلمات المرور كنصوص عادية<br>
إذا خُزّنت كلمات المرور دون تشفير، يمكن للمهاجمين الوصول إليها بسهولة إذا تم اختراق قاعدة البيانات.<br><br>

6- إنشاء كلمات مرور ضعيفة<br>
تخيل عم تستخدم لسا كلمات سر متل اسمك واسم الكراش🤦‍♂️، أو إذا مافي فرض قواعد صارمة لكلمات المرور ممكن يخلي الحسابات عرضة للهجمات.<br><br>

7- تخزين بيانات غير مشفرة في قاعدة البيانات<br>
مثل كلمات المرور، إذا خُزّنت بيانات حساسة (مثل أرقام البطاقات البنكية) بدون تشفير، يمكن سرقتها بسهولة.<br><br>



8- الاعتماد المفرط على جانب العميل<br>
الاعتماد على JavaScript في المتصفح للتحقق من البيانات (مثل التحقق من صحة النموذج) بدون التحقق بال Server بيسمح للمهاجمين بتجاوز هذه القيود.<br><br>



9- التفاؤل الزائد بشأن الأمان<br>
بعض المبرمجين بيتجدعنو وبيفترضوا انو مافي التطبيق آمن ومو بحاجة اختبار🌚.<br>
</p>
<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/7.png' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

10- السماح بتمرير المتغيرات عبر مسار URL<br>
إذا تمررت بيانات حساسة (مثل ال user-id) عبر عنوان URL دون تشفير، يمكن للمهاجمين التلاعب بها.<br><br>



11- الثقة المفرطة في الكود الخارجي<br>
استخدام مكتبات أو أكواد من مصادر غير موثوقة ممكن يسبب إدخال ثغرات أمنية.<br><br>



12- تضمين حسابات خلفية (Backdoor Accounts) مشفرة بشكل ثابت<br>
إضافة حسابات إدارية مخفية في الكود مع كلمات مرور ثابتة يسهل على المهاجمين اكتشافها.<br><br>



13- عدم التحقق من هجمات حقن SQL<br>
إذا ما نظفت مدخلات المستخدم ممكن يسمح للمهاجمين بحقن أوامر SQL للوصول إلى بيانات قاعدة البيانات.<br><br>



14- تضمين ملفات عن بُعد (Remote File Inclusions)<br>
السماح للتطبيق بتحميل ملفات من مصادر خارجية دون التحقق منها ممكن يسبب تنفيذ كود ضار.<br><br>



15- التعامل غير الآمن مع البيانات<br>
نقل البيانات الحساسة دون تشفير (مثل عبر HTTP بدلاً من HTTPS) يعرضها للاختراق.<br><br>



16- فشل في تشفير البيانات بشكل صحيح<br>
إذا استخدمت خوارزميات تشفير ضعيفة أو قديمة بخلي البيانات عرضة للكسر.<br>



17- عدم استخدام نظام تشفير آمن<br>
تجاهل معايير التشفير الحديثة (مثل AES أو RSA) يعرض البيانات للخطر.<br><br>



18- تجاهل الطبقة الثامنة (Layer 8)<br>
الطبقة الثامنة تشير إلى العامل البشري (مثل أخطاء المستخدمين أو المطورين). تجاهل تدريب المستخدمين أو المطورين بيرفع من المخاطر.<br><br>



19- عدم مراجعة تصرفات المستخدمين<br>
عدم مراقبة أو تسجيل أنشطة المستخدمين يجعل من الصعب اكتشاف الهجمات أو السلوكيات الضارة.<br><br>



20- إعدادات خاطئة لجدار الحماية لتطبيقات الويب (WAF)<br>
إعداد جدار حماية التطبيق بشكل غير صحيح قد يسمح بمرور الهجمات التي كان من المفترض منعه.<br><br>
</p>

---

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

وهلق رح نحكي عن اشهر 10 ثغرات بعالم تطبيقات الويب ورح ضيف شرح بسيط على كل وحدة منهم بس رح يكون لكل ثغرة درس لحال:<br><br>

1- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Broken Access Control </strong> </span>: <br>
لما المستخدمين بيقدروا يوصلوا لبيانات او وظائف ما عندهن الصلاحية من انهن يوصلولها متل عرض ملف شخصي لمستخدم تاني بتغيير ال user-id من ال URL.<br><br>
2- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Cryptographic Failures </strong> </span>: <br>
سرقة البيانات بسبب عدم استخدام تشفير قوي لحماية البيانات الحساسة(متل كلمات السر او بيانات العملاء)<br><br>
3- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Injection </strong> </span>: <br>
بيسمح هاد النوع من الثغرات للمهاجمين بإضافة اكواد واوامر داخل التطبيق (متل اوامر SQL) وهالشي بيسمح للمهاجم بسرقة وتسريب البيانات الحساسة.<br><br>
4- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Insecure Design </strong> </span>: <br>
لما المبرمج بيترك الأمان وبيعتبره شي ثانوي.<br><br>
5- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Security Misconfiguration </strong> </span>: <br>
ترك الإعدادات الافتراضي وكلمات السر الإفتراضية أو ترك البرمجيات قديمة.<br><br>
6- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Vulnerable and Outdated Components </strong> </span>: <br>
استخدام برمجيات او مكتبات قديمة ممكن يكون فيها ثغرات امنية.<br><br>
7- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Identification and Authentication Failures </strong> </span>: <br>
متل السماح بإنشاء حسابات بكلمات السر الضعيفة او عدم استخدام المصادقة المتعددة.<br><br>
8- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Software and Data Integrity Failures </strong> </span>: <br>
عدم التحقق من سلامة البيانات أو البرمجيات (مثل تحديثات غير موثوقة) قد يؤدي إلى إدخال كود ضار.<br><br>
9- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Security Logging and Monitoring Failures </strong> </span>: <br>
اذا ما سجلت الأنشطة المشبوهة أو مراقبتها هالشي بيترك اكتشاف الهجمات صعبًا.<br><br>
10- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Server-Side Request Forgery - SSRF </strong> </span>: <br>
بيسمح للمهاجمين بإجبار ال Server على إرسال طلبات لمواقع غير مصرح بها، وهالشي ممكن يكشف بيانات حساسة.<br>
</p>

<h2 id="Front End Components" dir=""><span class="me-2"><strong>Front End Components</strong></span><a href="#Front End Components" class="anchor text-muted"></a></h2>

<h2 id="📌 HTML:" dir=""><span class="me-2"><strong>📌 HTML:</strong></span><a href="#📌 HTML:" class="anchor text-muted"></a></h2>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

HTML(HyperText Markup Language) هي المكون الأساسي والأكثر أهمية بال Front end، وهي الطبقة الأساسية لأي Web Application ممكن نشوفه على الانترنت، وبتحدد ال HTML، الاساسيات العامة للصفحة متل العناوين (Titles) والصور (Images) والفقرات (Paragraphs) وكل العناصر الأساسية لتشكيل الصفحة.<br><br>
لما تتحمل صفحة الويب، المتصفح متل Firefox بفسر هي العناصر وبحولها لمحتوى مرئي للمستخدم النهائي.<br>
<span style="  color:rgb(221, 39, 78); font-size: 27px; line-height: 1.6;"><strong>مثال لصفحة HTML:</strong></span><br>
هي كود بسيط بيشرح كيف بتشتغل لغة ال HTML:
</p>
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page Title</title>
    </head>
    <body>
        <h1>A Heading</h1>
        <p>A Paragraph</p>
    </body>
</html>
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

الشي يلي بيظهر على المتصفح:
</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/10.jpg' | relative_url }}" alt="HTB">
</div>

---

<h3 id="⚪ HTML Structure" dir=""><span class="me-2" style="color:white"><strong>⚪ HTML Structure</strong></span><a href="#⚪ HTML Structure" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

بتتنظم عناصر HTML على شكل شجرة (Tree Structure)، بطريقة مشابهة للغات أخرى مثل XML. هذه الشجرة تبدأ من العنصر الجذر (document)، وتتفرع كما يلي:
</p>

```text
document
 - html
   -- head
      --- title
   -- body
      --- h1
      --- p
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
<span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>document: </strong> </span>
هو الجذر يلي بيحتوي على كامل الصفحة.<br>
<span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>html: </strong> </span>
العنصر الرئيسي يلي بيحتوي على كل عناصر الصفحة.<br>
<span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>head: </strong> </span>
يحتوي على عناصر غير مرئية مباشرة على الصفحة، مثل عنوان الصفحة (title).<br>
<span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>body: </strong> </span>
يحتوي على العناصر المرئية، متل العناوين (h1) والفقرات (p).<br><br>

كل عنصر في HTML يمكن أن يحتوي على عناصر أخرى داخلية، لكن العنصر html هو العنصر الأساسي الذي يضم جميع العناصر الأخرى في الصفحة. وهيك بقدر ميز مستندات HTML عن مستندات لغات تانية مثل XML.

</p>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/11.png' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
كل عنصر بلغة HTML بيتعرف عن طريق وسم (Tag) ليحدد نوعه. مثلاً:<br>
عندي وسم _p_ بيستخدم للفقرات، بيبدأ العنصر بوسم _p_ وبتنتهي بإغلاقه _/p_ والمحتوى بكون بين الوسمين
</p>
```html
<p>Hack With Farouk</p>
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
وممكن ضيف id او class للtag لحدد العنصر اكتر، متل:
</p>
```html
<p id="para1">One</p>
<p class="para2">Two</p>
```
---
<h3 id="⚪ URL Encoding" dir=""><span class="me-2" style="color:white"><strong>⚪ URL Encoding</strong></span><a href="#⚪ URL Encoding" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
 <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>URL Encoding </strong> </span>
 أو <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>(Percent-Encoding) </strong> </span>
 هو عبارة عن تحويل الأحرف الغير آمنة بال URLs لتنسيق ممكن المتصفحات انو تفهمه.<br> المتصفحات بتستخدم ترميز <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">ASCII</span>
 ، وهاد الترميز ما بيحتوي غير على الأحرف الأبجدية والأرقام (Alphanumeric)  وشوية رموز. وأي محارف تانيةلازم تترمز باستخدام رمز النسبة المئوية (<span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">%</span>) متبوعًا برقمين سداسي عشري (Hexadecimal).<br><br>
 المتصفح بحاجة انو يعرف مجموعة المحارف المستخدمة حتى يقدر يعرضها مزبوط وبعض المحارف متل المسافات او الرموز مابيقدر المتصفح انو يفهمها لهيك بتتحول لتنسيق آمن ومفهوم.<br>
 على سبيل المثال ال single-quote character ( <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">'</span> ) بيتحول ل <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>27%</strong></span>
 حتى يكون مفهوم بال URLs، وهي قائمة ببعض الرموز يلي بيتم تحويلها:<br><br>

</p>
	

| Character | Encoding | 
|---|---|---|
| space | %20 | 
| ! | %21 |
| " | %22 |
| # | %23 |
| $ | %24 |
| % | %25 |
| & | %26 |
| ' | %27 |
| ( | %28 |
| ) | %29 |




<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
في كتير ادوات لعمل ال Encoding وال Decoding لل URLs متل اداة ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Burb Suite</strong> </span> وادوات اونلاين متل: 
<a href="https://www.url-encode-decode.com/" target="_blank" rel="noopener noreferrer" style="font-size:20px">URL-Encoder</a><br>
فوت وجرب تعمل <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Encoding</strong> </span> لكلمة Hello World مثلاً وشوف شو بتصير وشو بيتغير فيها...
</p>

---

<h3 id="⚪ DOM" dir=""><span class="me-2" style="color:white"><strong>⚪ DOM</strong></span><a href="#⚪ DOM" class="anchor text-muted"></a></h3>
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
خلينا نقول انو اهو عبارة عن خريطة يلي بتعمل هيكلية صفحة ال HTML، او فينا نقول بشكل ادق هو الطريقة يلي بشوف فيها المتصفح صفحة ال HTML.<br>
وبتنقسم ال DOM ل 3 أنواع:<br>
1- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Core DOM: </strong> </span> لجميع انواع المستندات.<br>
2- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>XML DOM: </strong> </span> لمستندات ال XML.<br>
3- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>HTML DOM: </strong> </span> لمستندات ال HTML (وهي يلي بتهمنا).<br><br>
باستخدام ال DOM بتقدر تشير للعناصر متل document.head او document.body.h1 يعني متل ما بتشير لأي ملف بجهازك.<br><br>
<span style="  color:rgb(221, 39, 78); font-size: 27px; line-height: 1.6;"><strong>طيب سؤال الك🌚</strong></span><br> اذا بدنا نغير لون عنوان &lt;h1&gt; باستخدام JavaScript، شو بتتوقع منكتب جوا الكود؟🌚<br>
فكر باسم العنصر باستخدام DOM مابتهم طريقة الاستدعاء حالياً.
<br><br>
ال HTML فيني قسمها بشكل اساسي لقسمين:<br>
1- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>الـ &lt;head&gt;</strong></span>:
هنا بتحط حاجات متل عنوان الصفحة (<strong>&lt;title&gt;</strong>)، روابط CSS (<strong>&lt;link&gt;</strong>)، أو كود JavaScript (<strong>&lt;script&gt;</strong>). يعني متل الكواليس ورا المسرح.
<br>
2- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>الـ &lt;body&gt;</strong></span>:
هون المحتوى يلي بتشوفه بالصفحة، متل العناوين (<strong>&lt;h1&gt;</strong>) والفقرات (<strong>&lt;p&gt;</strong>) وحتى الصور (<strong>&lt;img&gt;</strong>)<br><br>

كل عنصر في الصفحة هو جزء من الـ <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>DOM</strong></span>
، وتقدر توصل له باستخدام الـ id أو class أو اسم الtag. ,وهالشي مفيد لو بدك تصلح مشكلة في الصفحة أو حتى تستغل ثغرة أمنية متل XSS (بس خلينا في الخير حالياً ورح نوصللها قريباً 😜).<br><br>
طيب لو ياترى شفت صفحة ويب فيها مشكلة انو في فقرة ماعم تظهر ياترى المشكلة بتكون بال <strong>&lt;head&gt;</strong> ولا بال <strong>&lt;body&gt;</strong>
</p>

<p dir="" style="color: white; font-size: 22px; line-height: 1.6;">
  <strong>HTB Questions:</strong>
</p>

<p style="font-size: 20px; line-height: 1.6;">
 What is the HTML tag used to show an image? 
</p>

<p dir="" style="color: white; font-size: 22px; line-height: 1.6;">
  <strong>Answer: &lt;img&gt;</strong>
</p>

---

<h2 id="📌 Cascading Style Sheets (CSS)" dir=""><span class="me-2"><strong>📌 Cascading Style Sheets (CSS)</strong></span><a href="#📌 Cascading Style Sheets (CSS)" class="anchor text-muted"></a></h2>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
تخيّل ال HTML عبارة عن الهيكل العظمي لصفحة الويب، متل البيت اللي بنيته بالطوب. هون بتجي ال، CSS متل اللي بييجي يدهن الجدران، يحط الستاير، يختار الألوان، ويخلي البيت حلو ومرتب<br>
يعني ال CSS هي اللغة يلي منستخدمها مشان نتحكم بشكل وتنسيق عناصر ال HTML من الألوان والخطوط والحجم ومكان العناصر بالصفحة وحتى الحركات وال Animation.<br>
<span style="  color:rgb(221, 39, 78); font-size: 27px; line-height: 1.6;"><strong>مثال بسيط:</strong></span><br>
</p>

```css
body {
  background-color: black;
}

h1 {
  color: white;
  text-align: center;
}

p {
  font-family: helvetica;
  font-size: 10px;
}
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
اول شي ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>body</strong></span>:
وهو يلي بيتحكم بهيكل الصفحة كلها، وهون حطينا الخلفية تكون باللون الأسود.<br>
بعدين عنا ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>h1</strong></span>:
وهون حطينا لون جميع العناوين بالأبيض ومكانها بمنتصف الشاشة. <br>
اول شي ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>p</strong></span>:
وهون خلينا كل الفقرات مكتوبة بخط Helvetica وبحجم 10px.
<br><br>
لو جربنا هاد الكود بصفحة ال HTML يلي عملناها قبل شوي رح تطلع احلى بكتير، بس بعرفك اكيد تكاسلت وماجربت ال HTML🌚<br>
يلا يا كسلان فوت جربهن بأيدك وجرب عدل عال css وشوف شو بصير😁
</p>

---

<h3 id="⚫ Syntax" dir=""><span class="me-2" style="color:white"><strong>⚫ Syntax</strong></span><a href="#⚫ Syntax" class="anchor text-muted"></a></h3>
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">

بتتذكر بال css نحنا وعم نحكي عن ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>tags</strong></span> قلنا انو منقدر نحطلهن id , class يعني مثلا &lt;p id="para1"&gt; ، ال CSS هو يلي بيستفيد من هالحركة بهالطريقة:
</p>

```css
#para1 {
  color: blue;
}
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
هون بقول لل CSS لو لقيت Paragraph ال id الخاص فيه para1 خلي الخط فيه ازرق، وهالشي مشان ما نفذ امر واحد لكل ال paragraphs.<br>
</p>
---
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
ابحث عالنت كيف بتقدر تحدد اوامر بناء على ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Class</strong></span> مو ال id، واذا عندي فقرة ال id تبعها para1 وفقرة تانية ال class تبعها para2 
كيف منقدر نخلي الاولى باللون الازرق والثانية بالاخضر، فكر لحالك لا تسأل Chatgpt شايفك🌚
 </p>
---
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
CSS بتنكتب بطريقة سهلة ومنظمة وكل قاعدة بتكون بهالشكل:
</p>

```css
h1 {
  color: white;
  text-align: center;
}
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
هون منلون كل عنصر <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>h1</strong></span> باللون الأبيض ومنخليه يتوسط الصفحة.<br>
وفي كتير <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>properties</strong></span> ممكن استخدمها بال css رح احكي عن بعض منها:<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>color</strong></span>: لون النص.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>background-color</strong></span>: لون الخلفية.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>font-size</strong></span>: حجم الخط.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>margin</strong></span>: المسافة الخارجية حول العنصر.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>padding</strong></span>: المسافة الداخلية داخل العنصر.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>border</strong></span>: الحدود حول العنصر.<br>
وكل خاصية في الها قيم معينة، متل الألوان (red, #FF0000) أو الأحجام (10px, 2em) أو كلمات مفتاحية (center, bold).
</p>

---
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
ابحث عالنت كيف منقدر نخلي فقرة عندها حدود سوداء ومسافة داخلية 5 بكسل، وشو الخصائص اللي لازم تستخدمها؟
 </p>
---
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
مامنستخدم ال CSS للألوان والتنسيق فقط، منقدر نستخدمها مشان نخلي الموقع يرقص💃🏻<br>
بتقدر تعمل حركات متل تغيير اللون بشكل تدريجي او تحرك العناصر او حتى تعمل رسومات <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">3D</span>.,<br><br>مثال بسيط:<br> </p>

```css
@keyframes slide {
  from { left: 0; }
  to { left: 100px; }
}

div {
  animation: slide 2s infinite;
}
```

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
هون منقول للعنصر div يتحرك من اليسار لليمين 100 بيكسل بثانيتين، وخليك عم تكرر الحركة للأبد، يعني مافي اسهل من هيك كأنك عم تدرب روبوت عالرقص😂💃🏻
</p>
---
<h3 id="⚫ Usage" dir=""><span class="me-2" style="color:white"><strong>⚫ Usage</strong></span><a href="#⚫ Usage" class="anchor text-muted"></a></h3>
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
بيشتغل متل سوبرمان مع ال HTML وال JavaScript:<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span>: بتقدر تغير أنماط العناصر بناء على تصرف المستخد، متل انك تضغط على زر فيتغير فيتغير لون الخلفية.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>HTML</strong></span>: بيخلي الصفحة تطلع أنيقة ومرتبة بدل ما تكون مجرد نصوص مملة.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>تطبيقات الموبايل</strong></span>: CSS بيستخدم بتصميم واجهات المستخدم (UI) لتطبيقات الموبايل.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>مع XML أو SVG</strong></span>: ممكن تستخدم CSS لتنسق عناصر متل الصور المتجهة.<br>
</p>
---
<h3 id="⚫ Frameworks" dir=""><span class="me-2" style="color:white"><strong>⚫ Frameworks</strong></span><a href="#⚫ Frameworks" class="anchor text-muted"></a></h3>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
كتابة قواعد لكل <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Element</span> ممكن يكون متعب وخاصة لو عم تشتغل على Project كبير لهيك في شي اسمه <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;">Frameworks</span> وهي قوالب جاهزة مليانة تصاميم حتى توفر عليك وقت وجهد وتخلي الصفحة احترافية بشكل اسرع.<br><br>
<strong>أشهر أطر العمل:</strong><br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Bootstrap</strong></span>: متل السوبرمان بتاع CSS، فيه كلشي  جاهز من أزرار لجداول.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>SASS</strong></span>: نسخة "مطورة" من CSS، بتخليك تكتب كود أقل وأذكى.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Foundation</strong></span>: متل Bootstrap بس أخف ومرن أكثر..<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Bulma</strong></span>: خفيف وسهل، مثالي للمشاريع الصغيرة.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Pure</strong></span>: بسيط وخفيف جدًا، للي بدهم شي minimal.<br><br>
الإطارات هي بتيجي مع قوالب جاهزة، متل أزرار، قوائم، أو حتى تصاميم كاملة لصفحات، وبتشتغل حلو مع JavaScript.
</p>
---
<h2 id="📌 JavaScript" dir=""><span class="me-2"><strong>📌 JavaScript</strong></span><a href="#📌 JavaScript" class="anchor text-muted"></a></h2>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
حكينا قبل انو ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>HTML</strong></span> هو الهيكل العظمي تبع صفحة الويب وال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>CSS</strong></span> هو الديكور والألوان يلي بتعطي جمالية للصفحة، اما ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> فهو العقل يلي بتخلي الصفحة تعيش وتتفاعل مع المستخدم.<br><br>
ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> هي لغة من اشهر لغات البرمجة بالعالم ومنستخدمها بشكل اساسي لتطوير تطبيقات الويب، غالباً بتشتغل ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> بال Front End يعني بالمتصفح تبعك، بس كمان ممكن انها تستخدم بال Back End متل لما نستخدمها مع ال Node.js. <br><br>
حرفيا بدون ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> صفحات الويب رح تكون متل لوحة قديمة، حلوة بس مافيها حياة، ومستحيل تتفاعل معك، اما باستخدام ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> بتخلي الصفحة تتفاعل معك يعني متل لما تضغط زر يتنفذ امر معين، او لما يتحدث المحتوى بالوقت الفعلي يعني متل تحديثات ال Timeline بالتويتر (X🌚).<br><br>
وفي طريقتين لكتابة كود <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span>:<br>
1- كتابة كود داخل صفحة ال HTML:
</p>
```html
<script type="text/javascript">
    document.getElementById("button1").innerHTML = "نص جديد!";
</script>
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
2- او ربط ملف <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> خارجي:
</p>
```html
<script src="./script.js"></script>
```
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
<span style="  color:rgb(221, 39, 78); font-size: 27px; line-height: 1.6;"><strong>مثال عملي:</strong></span><br>
مافي داعي تفهم المثال كتير، بس المهم تفهم شو بتعمل ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> ومع الوقت رح تفهم اللغة اكتر🌚
</p>
```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript</title>
</head>
<body>
    <button id="button1">Click Here</button>
    <script type="text/javascript">
        document.getElementById("button1").onclick = function() {
            document.getElementById("button1").innerHTML = "Contant Changed!";
        };
    </script>
</body>
</html>
```
<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/12.png' | relative_url }}" alt="HTB">
</div>

<div class="htblogo">
  <img src="{{ '/images/HTB/IntroToWebApplications/13.png' | relative_url }}" alt="HTB">
</div>

<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
لنفرض عندي هي صفحة ال HTML، فيها زر ال id = button1 ، الكود بقول لما تضغط على هاد الزر غير النص داخله ل Contant Changed!، وفي كتير مواقع ممكن تجرب فيهن استخدام ال JavaScript متل موقع
</p>
[jsfiddle](https://jsfiddle.net/)
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
يلي بيسمحلك تكتب html, css, javascript، وتشوف الناتج.
</p>
<h3 id="🟡 Usage" dir=""><span class="me-2" style="color:white"><strong>🟡 Usage</strong></span><a href="#🟡 Usage" class="anchor text-muted"></a></h3>
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
بتشتغل ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> جوا المتصفح بفضل محرك داخل المتصفحات وهو متل شيف بيطبخ الكود وبحوله لتعليمات تتنفذ عجهازك مباشرة بدون ما تحتاج ترجع للسيرفر، وهاد الشي بخلي ال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span> سريعة جدا لأن كلشي بصير على جهازك، يعني متل لما تحط Like لحدا على الانستغرام فهو يلي بحول القلب للون الأحمر🌚❤️<br>
او حتى لما تشوف كيف اللايكات عم تزيد بدون ما تحتاج تعيد تحميل الصفحة
</p>

<h3 id="🟡 Frameworks" dir=""><span class="me-2" style="color:white"><strong>🟡 Frameworks</strong></span><a href="#🟡 Frameworks" class="anchor text-muted"></a></h3>
<p dir="rtl" style=" font-size: 22px; line-height: 1.6;">
متل ماحكينا بال CSS هي عبارة عن ادوات فيها اكواد ومكاتب جاهزة حتى توفر وقت وجهد وبتساعد تبني التطبيق بسرعة، ومن اشهر ال Frameworks الخاصة بال <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>JavaScript</strong></span>:<br><br>

- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>React</strong></span>: سريع ومرن، وبيستخدمه ناس كتير متل فيسبوك.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Angular</strong></span>: لتبني تطبيقات كبيرة بطريقة منظمة.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>Vue</strong></span>: خفيف وحلو، مثالي للمشاريع اللي عايزة شي بسيط بس قوي.<br>
- <span style="  color:rgb(138, 201, 38); font-size: 20px; line-height: 1.6;"><strong>jQuery</strong></span>: الأخ الأكبر، كان مشهور زمان ومازال مفيد لأشياء بسيطة.<br><br>
كل إطار عمل عنده مميزات خاصة، وتقدر تشوف المقارنة بينهم:
</p>
[wikipedia](https://en.wikipedia.org/wiki/Comparison_of_JavaScript-based_web_frameworks)

<h2 id="Front End Vulnerabilities" dir=""><span class="me-2"><strong>Front End Vulnerabilities</strong></span><a href="#Front End Vulnerabilities" class="anchor text-muted"></a></h2>

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