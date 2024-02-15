🌍
*[Čeština](README-cs.md) ∙ [Deutsch](README-de.md) ∙ [Ελληνικά](README-el.md) ∙ [English](README.md) ∙ [Español](README-es.md) ∙ [Français](README-fr.md) ∙ [Indonesia](README-id.md) ∙ [Italiano](README-it.md) ∙ [日本語](README-ja.md) ∙ [한국어](README-ko.md) ∙ [polski](README-pl.md) ∙ [Português](README-pt.md) ∙ [Română](README-ro.md) ∙ [Русский](README-ru.md) ∙ [Slovenščina](README-sl.md) ∙ [Українська](README-uk.md) ∙ [简体中文](README-zh.md) ∙ [繁體中文](README-zh-Hant.md) ∙ [فارسی](README-fa.md)*


# هنر خط فرمان

- [متا](#متا)
- [مبانی](#مبانی)
- [Everyday use](#everyday-use)
- [Processing files and data](#processing-files-and-data)
- [System debugging](#system-debugging)
- [One-liners](#one-liners)
- [Obscure but useful](#obscure-but-useful)
- [macOS only](#macos-only)
- [Windows only](#windows-only)
- [More resources](#more-resources)
- [Disclaimer](#disclaimer)

![curl -s 'https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md' | egrep -o '`\w+`' | tr -d '`' | cowsay -W50](cowsay.png)


تسلط در خط فرمان مهارتی است که اغلب نادیده گرفته می شود یا به عنوان یک مهارت محرمانه در نظر گرفته می شود، اما انعطاف پذیری و بهره وری شما را به عنوان یک مهندس به دو روش واضح و ظریف بهبود می بخشد. این مجموعه ای از یادداشت ها و نکات در مورد استفاده از خط فرمان است که در هنگام کار بر روی لینوکس مفید بوده است. برخی نکات ابتدایی هستند و برخی نسبتاً خاص، پیچیده یا مبهم هستند. این صفحه طولانی نیست، اما اگر بتوانید از همه موارد اینجا استفاده کنید و به خاطر بیاورید، چیزهای زیادی می دانید.


این اثر حاصل [بسیاری از نویسندگان و مترجمان] (AUTHORS.md) است.
برخی از این
[اصل](http://www.quora.com/What-are-some-lesser-known-but-useful-Unix-commands)
[ظاهر شد](http://www.quora.com/What-are-the-the-best-full-Swiss-army-knife-one-liners-on-Unix)
در [Quora](http://www.quora.com/What-are-some-time-saving-tips-that-every-Linux-user-should-know)،
اما از آن زمان به GitHub منتقل شده است، جایی که افراد با استعدادتر از نویسنده اصلی، پیشرفت های زیادی را ایجاد کرده اند.
[**لطفاً سوالی ارسال کنید**](https://airtable.com/shrzMhx00YiIVAWJg) اگر سوالی در رابطه با خط فرمان دارید. [**لطفا مشارکت کنید**](/CONTRIBUTING.md) اگر خطایی یا چیزی که می‌تواند بهتر باشد مشاهده کردید!


## متا

محدوده:

- این راهنما هم برای کاربران مبتدی و هم برای کاربران با تجربه است. اهداف عبارتند از *عرض* (همه چیز مهم)، *ویژگی* (نمونه های ملموس از رایج ترین مورد را ارائه دهید)، و *خلاصه* (از چیزهایی که ضروری نیستند یا انحرافاتی که به راحتی می توانید در جای دیگری جستجو کنید) اجتناب کنید. هر نکته در برخی شرایط ضروری است یا به طور قابل توجهی باعث صرفه جویی در زمان نسبت به گزینه های جایگزین می شود.
- این برای لینوکس نوشته شده است، به استثنای بخش های "[macOS only](#macos-only)" و "[Windows only](#windows-only)". بسیاری از موارد دیگر اعمال می شوند یا می توانند روی Unices یا macOS دیگر (یا حتی Cygwin) نصب شوند.
- تمرکز روی Bash تعاملی است، اگرچه نکات بسیاری در مورد سایر پوسته ها و اسکریپت نویسی عمومی Bash اعمال می شود.
- شامل دستورات "استاندارد" یونیکس و همچنین دستوراتی است که به نصب بسته خاصی نیاز دارند -- تا زمانی که به اندازه کافی مهم باشند که شایستگی گنجاندن آنها را داشته باشند.

یادداشت:

- برای نگه داشتن این در یک صفحه، محتوا به طور ضمنی با مرجع درج می شود. شما آنقدر باهوش هستید که به محض اطلاع از ایده یا دستور به Google، جزئیات بیشتری را در جای دیگری جستجو کنید. برای نصب برنامه های جدید از «apt»، «yum»، «dnf»، «pacman»، «pip» یا «brew» (در صورت لزوم) استفاده کنید.
- از [Explainshell] (http://explainshell.com/) برای دریافت اطلاعات مفیدی از آنچه دستورات، گزینه‌ها، لوله‌ها و غیره انجام می‌دهند استفاده کنید.

## مبانی

- بش (bash) اولیه را یاد بگیرید. در واقع «man bash» را تایپ کنید و حداقل همه چیز را مرور کنید. پیگیری آن بسیار آسان است و چندان طولانی نیست. پوسته های جایگزین می توانند خوب باشند، اما Bash قدرتمند و همیشه در دسترس است (آموزش *فقط* zsh، ماهی و غیره، در حالی که روی لپ تاپ شما وسوسه انگیز است، شما را در بسیاری از موقعیت ها محدود می کند، مانند استفاده از سرورهای موجود).