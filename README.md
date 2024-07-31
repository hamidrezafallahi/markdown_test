## پروژه برنامه ریزی منابع سازمان ساخته شده توسط شرکت آرین سیستم

## شروع این پروژه

اول باید سرور توسعه رو اجرا کنید :

```bash
npm run dev
```

-یا-

```bash
 yarn dev
```

لینک [http://localhost:3000] را با مرورگر خود باز کنید تا نتیجه را ببینید.
شما میتوانید محتوای صفحات را ویرایش کنید با شروع تغییر در فایل `app/page.tsx`.صفحه بصورت خودکار بروز میشود اگر شما تغییراتی را اعمال کنید .
ادرس سایت پابلیش شده <a name="TOP"></a>

---

# لیست تنظیمات صورت گرفته

ساخته شده توسط فریمورک nextjs با typescript و بصورت approuter : "next": "14.2.3"

چند زبانگی و تنظیم زمان بر اساس منطقه ورود به سایت : "next-intl": "^3.15.3"

استفاده از کتابخانه ant design : "antd": "^5.18.3"

تنظیمات service worker & pwa : "@ducanh2912/next-pwa": "^10.2.7"

کتابخانه استایل دهی : "tailwindcss": "^3.4.1","tailwind-scrollbar": "^3.1.0"

کتابخانه تست نویسی:"jest": "^29.7.0","ts-jest": "^29.1.4","@testing-library/react": "^15.0.7","@testing-library/jest-dom": "^6.4.5",

کتابخانه تبدیل تایپ اسکریپت به جاوا اسکریپت : "@babel/preset-typescript": "^7.24.6"

کتابخانه کنترل ورودی و خروجی :"typescript": "^5","ts-node": "^10.9.2"

# ساختار پروژه

---

پوشه **test** برای تست نویسی با ساختار filebase تنظیم شده.

پوشه .next بصورت پیشفرض توسط next ساخته میشود.

پوشه app ریشه اصلی صفحات برنامه میباشد.

پوشه components با قالب atomic design تنظیم شده که دارای زیرمجموعه های atoms molecules organisms templates میباشد.

پوشه Layout برای قالب بندی پروژه بر اساس دستگاه ورود کننده و حذف المانهای غیر نیاز طبق دستگاه میباشد.

پوشه message طبق ساختار globalization بر اساس زبان منطقه قرار است متن صفحات رو بصورت json برگرداند.

پوشه node_module که محل نگهداری تمامی کتابخانه ها میباشد.

پوشه public محل نگهداری تنظیمات و دارایی ها و عکس ها و فونت ها و سرویس ورکر و آیکون میباشد.

پوشه services قسمتی از حافظه که با کمک RTK Query درخواستهای ما را مدیریت و نگهداری میکند.

پوشه slices قسمت دیگر حافظه که با کمک Redux وظیفه ی ذخیره و نگهداری مقادیر جاری در سایت و ورودی ها را دارد.

پوشه store که وظیفه ی به هم چسباندن قطعات حافظه و پوشاندن کل پروژه از اطلاعات خود را دارد .

پوشه styles محل نگه داری استایل دهی ها میباشد.

پوشه types محل نگهداری تایپ ها و اینتر فیس ها میباشد.

پوشه utils محل نگهداری ماژول ها و توابع کاربردی پروژه میباشد .

# فایل های تنظیمات اولیه

---

فایل .env : فایل ذخیره و مدیریت مقادیر پیشفرض مثل آدرس سرور یا کد رمزنگاری

فایل eslintrc.json تنظیمات eslint هست که کد شما را برای خطاهای احتمالی تجزیه و تحلیل میکند.

فایل .gitignore تنظیمات پیشفرض گیت برای جلوگیری از ارسال و دریافت فولدر های با حجم بالا و غیر ضروری همچون node_module .

فایل babel.config تنظیمات مترجم تایپ اسکریپت به جاوا اسکریپت ساده .

فایل firebase.js تنظیمات برقراری ارتباط با سرور firebase .

فایل i18n.js تنظیمات واکشی فایل جیسون چند زبانه بر اساس منطقه ورود.

فایل jest.config.tsx تنظیمات تست نویسی برای فایل های تایپ اسکریپت .

فایل middleware.ts محل کنترل دسترسی کاربران به صفحات بر اساس نقش آنها.

فایل next.config.js محل تنظیمات اصلی برنامه مثل webpack,globalization,pwa.

فایل package.json فایل شناسنامه پروژه و محل معرفی نام و نسخه و کتابخانه های به کار رفته در پروژه.

فایل postcss.config فایل تنظیمات مترجم فایل های استایل دهی از جاوا اسکریپت.

فایل tailwind.config فایل تنظیمات پیشفرض استایل دهی به پروژه.

فایل tsconfig.test فایل تنظیمات مفسر تایپ اسکریپت.

# تنظیمات کتابخانه ها

---

<!-- تنظیمات زبان برنامه  -->

# تنظیمات globalization

ابتدا نیاز به نصب یکی از کتابخانه های i18n رو دارید .
ما در این پروژه از کتابخانه ی next-intl استفاده میکنیم.

```bash
npm install next-intl
```

که معماری پوشه بندی رو به شکل زیر درمی آورد .

```

├── message (1)
│   ├── fa.json
│   ├── en.json
│   └── ...
├── next.config.mjs (2)
├── i18n.ts (3)
├── middleware.ts (4)
└── app
    └── [locale]
        ├── layout.tsx (5)
        └── page.tsx (6)
```

بعد از بوجود آوردن پوشه message داخل آن به تعداد زبانهایی که برنامه قرار است پشتیبانی کند فایل جیسون ساخته ونام فایل جیسون باید دقیقا برابر با دو حرف اول زبان منطقه ی ورود به سایت باشد

### en.json

```
{
  "HomePage": {    //نام صفحه مورد نظر
    "title": "Hello world!" // نام متن
  }
}
```

### fa.json

```
{
  "HomePage": {    //نام صفحه مورد نظر
    "title":"نام متن به همراه خود متن// "سلام دنیا
  }
}
```

## next.config.js

```
const createNextIntlPlugin = require("next-intl/plugin");

const composedConfig = createNextIntlPlugin(withPWA(nextConfig));

module.exports = composedConfig;
```

## i18n.js

```
 import {getRequestConfig} from 'next-intl/server';

export default getRequestConfig (async ({locale}) => {

  const locales = ['en', 'fa'];

  const currLocale=locales.includes(locale)?locale:"fa"

    return {

        messages: (await import(`./message/${currLocale}.json`)).default

    }

});


```

## middleware.ts

```
import { NextRequest } from 'next/server';

import createMiddleware from 'next-intl/middleware';

export default async function middleware(request: NextRequest) {

  const handleI18nRouting = createMiddleware({

    locales: ['en', 'fa'],

    defaultLocale: 'fa'

  });

  const response = handleI18nRouting(request);

  return response;
}
```

## تغییر پوشه بندی داخلی پوشه صفحات بصورت داینامیک و دریافت locale

```
└── app
    └── [locale]
        ├── layout.tsx (5)
        └── page.tsx (6)
```

## انتشار مقدار locale در تمامی مسیر های زیر مجموعه در قالب props

```
'use client'
import LOADING from "@components/atoms/LOADING";
import Theme from "@components/templates/Theme";
import DashboardLayout from "@layout/mainLayout/desktopSizeLayout/dashboardLayout/layout";
import ReduxProvider from "@redux/Provider";
import { NextIntlClientProvider } from "next-intl";
import { usePathname } from "next/navigation";
import { ReactNode, Suspense } from "react";
const DesktopLayout = (props: { children: ReactNode, local: string }) => {
    const { children, local } = props
    const route = usePathname()
    return (
        <NextIntlClientProvider  locale={local}>
        <ReduxProvider >
            <Theme>

                {
                    route.endsWith(`/${local}`) ? <>{children}</> :
                        <DashboardLayout>
                            <Suspense fallback={<LOADING />}>{children}</Suspense>
                        </DashboardLayout>
                }
            </Theme>
        </ReduxProvider>
        </NextIntlClientProvider>
    );
}

export default DesktopLayout
    ;
```

### و در نهایت برای استفاده از متن در یک صفحه به شکل زیر عمل میکنیم

---

```
import {useTranslations} from 'next-intl';

export default function HomePage() {

const t = useTranslations('HomePage');    //نام صفحه ترجمه شده

return <h1>{t('title')}</h1>;         //انتخاب نام متن
}
```

    ├── message (1)
    │   ├── fa.json
    │   ├── en.json

```
    {
  "HomePage": {    //نام صفحه مورد نظر
    "title": "Hello world!" // نام متن
                }
    }
```

---

<!-- منطق پوشه بندی کامپوننت ها  -->

# منطق پوشه بندی کامپوننت ها

---

پوشه بندی داخل کامپوننت ها به صورت زیر میباشد

```
 ├── components                     //پوشه اصلی کامپوننتها
 |   ├── atoms                      //کوچکترین جزء یک ساختار رو در اینجا ذخیره میکنند
 |   |   ├── defaultElements        //کامپوننت های پیشفرض پروژه در این پوشه هستند
 |   |   |   ├── BTN                //کامپوننت دکمه برگرفته از Ant Design
 |   |   |   |   ├── index.tsx      // فایل اصلی کامپوننت به همراه تمامی صفات
 |   |   |   |   └── interface.ts   //فایل تایپ کامپوننت به همراه تایپ صفتهای آن
 |   |   |   ├── INPUT              //کامپوننت ورودی برگرفته از Ant Design
 |   |   |   |   └── index.tsx
 |   |   |   └── ...
 |   |   ├── iconComponents         //پوشه تمامی آیکونها که تبدیل به کامپوننت شدند برای تغییر و استایل دهی راحت تر
 |   |   |   ├── PlusOutline.tsx
 |   |   |   └── ...
 |   |   └── ...
 |   ├── molecules                  //محل ذخیره ی گروه کامپوننت ها که از ترکیب بیش از یک جزء بوجود می آید
 |   |   ├── SearchBox.tsx          //متشکل از یک ورودی و یک دکمه
 |   |   └── ...
 |   ├── organisms                  //محل ذخیره ی اجزایی مثل جدول و فرم که از ترکیب گروه کامپوننتها بوجود می آید
 |   |   ├── login.tsx              //کامپوننت فرم ورود با تمام منطق ها و validations
 |   |   ├── signout.tsx            //کامپوننت فرم ثبت نام  با تمام منطق ها و validations
 |   |   └── ...
 |   └── templates                  //محل ذخیره ی کامپوننت ها که اعضای یک صفحه هستند
 |       ├── auth.tsx               //کامپوننتی متشکل از دو فرم که عملیات ورود و ثبت نام را هندل میکند
 |       └── ...
```

# قالب بندی بر اساس دستگاه

---

اگر شما با موبایل به سایت وارد شوید نیازی به ساید بار ندارید.
همچنین اگر با دسکتاپ وارد سایت شوید نیازی به navigation bar نخواهید داشت.
از این رو برای حذف کامل المانهای غیر ضروری صفحه با توجه به user-agent موجود در header میتوان نوع دستگاه را تشخیص داده و نوع قالب بندی سایت را تغییر دهیم
برای انجام این کار نیاز است در لایه های بالا این مقدار را مطابق کد زیر گرفته و مقایسه کنیم و در صورت وجود یا عدم وجود شرط لایه متناسب با دستگاه را بارگزاری کنیم و از رندر اعضای مخفی شده در DOM جلوگیری به عمل آوریم.
در این پروژه یک پوشه جداگانه از کامپوننتها و صفحات برای اعضای خاص که در موبایل و دسکتاپ متغیر میباشند بوجود آورده و این مساله رو در آن پوشه مدیریت میکنیم .

```
import React from "react";
import BaseLayout from "../../layout/baseLayout/layout";
import { headers } from "next/headers";
export default async function BodyLayout({ children, params: { local } }: { children: React.ReactNode; params: { local: string } }) {
  const headersList = headers()
  const userAgent = headersList.get("user-agent");
  const deviceType = userAgent?.match(/Mobile|Android|iPhone|iPad|iPod|Opera Mini|BlackBerry|IEMobile/) ? 'mobile' : 'desktop';
  return (<html lang={local}>
    <body dir={local === 'fa' || local === undefined ? "rtl" : ""} >
      <BaseLayout viewport={deviceType} local={local}>
        {children}
      </BaseLayout>
    </body>
  </html>
  );
}
```

و در نهایت در لایه اصلی دو لایه موبایل و دسکتاپ رو از همدیگر جدا میکنیم

```
import { ReactNode } from "react";
import "../../styles/globals.css";
import DesktopSizeLayout from "../mainLayout/desktopSizeLayout";
import MobileSizeLayout from "../mainLayout/mobileSizelayout";
import ReduxProvider from "@redux/Provider";

const BaseLayout = (props: { children: ReactNode, viewport: string ,local:string }) => {
    const { children, viewport,local } = props
    return (<>
        {
            viewport === "desktop" ?
                <DesktopSizeLayout local={local}>
                    {children}
                </DesktopSizeLayout>
                :
                <MobileSizeLayout>
                    {children}
                </MobileSizeLayout>
        }
    </>);
}
export default BaseLayout;
```

.که در هر لایه مخصوص المانهایی وجود دارند که تنها در همان لایه رندر میشوند

.همچنین در این لایه تمامی تامین کننده ها رو که مقادیرشان باید در تمام پروژه در دسترس باشد ،اضافه میکنیم

تامین کنندگانی مثل theme ,store ,locale,...

```
'use client'
import LOADING from "@components/atoms/LOADING";
import Theme from "@components/templates/Theme";
import DashboardLayout from "@layout/mainLayout/desktopSizeLayout/dashboardLayout/layout";
import ReduxProvider from "@redux/Provider";
import { NextIntlClientProvider } from "next-intl";
import { usePathname } from "next/navigation";
import { ReactNode, Suspense } from "react";
const DesktopLayout = (props: { children: ReactNode, local: string }) => {
   const { children, local } = props
   const route = usePathname()
   return (
       <NextIntlClientProvider  locale={local}>
       <ReduxProvider >
           <Theme>

               {
                   route.endsWith(`/${local}`) ? <>{children}</> :
                       <DashboardLayout>
                           <Suspense fallback={<LOADING />}>{children}</Suspense>
                       </DashboardLayout>
               }
           </Theme>
       </ReduxProvider>
       </NextIntlClientProvider>
   );
}
export default DesktopLayout
```

# public

در این پوشه اطلاعات قابل تغییر پروژه قرار میگیرد

> تنظیمات آدرس سرور.

> آیکون نرم افزار.

> تنظیمات سرویس ورکر.

> تنظیمات firebase.

> تنظیمات PWA.

## assets

محل نگهداری عکس ها ،فونتها و آیکونها

### fonts

محل ذخیره سازی فونتها

### svgs

محل ذخیره سازی آیکون ها برگرفته از فیگما

### AppSetting

محل تغییر آدرس سرور ، به علت در دسترس بودن حتی بعد از build برنامه در اینجا تنظینات نگهداری میشود.

### firebase massaging

محل ذخیره سازی تنظیمات سرور اعلان ها

### manifest

محل ذخیره سازی تنظیمات PWA

### robots.txt

محل تنظیمات خزنده های جستجوگر

<!-- services -->

## سرویس ها

یکی از دو قسمت اصلی حافظه میباشد که کار مدیریت درخواستها را بر عهده دارد.

از کتابخانه ی `RTK QUERY` بابت مدیریت درخواستها استفاده شده .
در صفحه ی `index.tsx` تمامی درخواستها ادغام میشود .
و به عنوان خروجی اصلی سرویس ها به `store` ارسال میشود .

### مدیریت ارور ها در پاسخ سرور

همگی بصورت اعلان باید نمایش داده شوند و مدیریت آن توسط یک middleware از درون خود ریداکس کوئری رخ میدهد.
که این middleware نیز بصورت جداگانه به `store` ارسال میشود.

این رفتار توسط فایل `rtkQueryErrorLogger`مدیریت میشود.
بدین صورت که متدی داخل ریداکس وجود دارد به نام `isRejectedWithValue` که دور درخواست پیچیده میشود به شکل زیر و در صورت پاسخ ارور یک فعالیتی را انجام میدهد.

```
export const rtkQueryErrorLogger: Middleware = () => (next) => (action) => {
  if (isRejectedWithValue(action)) {
    if (action.payload.status !== 401) {
        //اینجا باید یه بار رفرش توکن با سرویس لاگین صدا زده بشه و پارامتر رفرش توکن فرستاده بشه
        //بعد اگه دوباره به همین ارور خورد پاپ اپ لاگین یا هدات شود به لندگینگ یا لاگین ...
    showToast({message:"The HTTP status code 401, often denoted as UNAUTHORIZED , signifies that the client lacks proper authentication credentials or has provided invalid credentials. In simpler terms, the server has failed to identify the user"})
    }
  }
  return next(action);
};

```

همچنین در قسمت middleware به store اضافه میگردد.

const ServiceRootReducer = () => {

    return {
        serviceReducer: {
            [comAuth.reducerPath]: comAuth.reducer,
            [ComAuthToken.reducerPath]: ComAuthToken.reducer,
        },
        serviceMiddleware: [
            comAuth.middleware,
            ComAuthToken.middleware,
            `rtkQueryErrorLogger`
        ]

    }

}

export default ServiceRootReducer;

# Markdown syntax guide

## Headers

# This is a Heading h1

## This is a Heading h2

###### This is a Heading h6

## Emphasis

_This text will be italic_  
_This will also be italic_

**This text will be bold**  
**This will also be bold**

_You **can** combine them_

## Lists

### Unordered

- Item 1
- Item 2
- Item 2a
- Item 2b

### Ordered

1. Item 1
2. Item 2
3. Item 3
   1. Item 3a
   2. Item 3b

## Images

![This is an alt text.](/image/sample.webp "This is a sample image.")

## Links

You may be using [Markdown Live Preview](https://markdownlivepreview.com/).

## Blockquotes

> Markdown is a lightweight markup language with plain-text-formatting syntax, created in 2004 by John Gruber with Aaron Swartz.
>
> > Markdown is often used to format readme files, for writing messages in online discussion forums, and to create rich text using a plain text editor.

## Tables

| Left columns | Right columns |
| ------------ | :-----------: |
| left foo     |   right foo   |
| left bar     |   right bar   |
| left baz     |   right baz   |

## Blocks of code

```
let message = 'Hello world';
alert(message);
```

## Inline code

This web site is using `markedjs/marked`.

# Markdown Cheatsheet<a name="TOP"></a>

---

# Heading 1

    Markup :  # Heading 1 #

    -OR-

    Markup :  ============= (below H1 text)

## Heading 2

    Markup :  ## Heading 2 ##

    -OR-

    Markup: --------------- (below H2 text)

### Heading 3

    Markup :  ### Heading 3 ###

#### Heading 4

    Markup :  #### Heading 4 ####

Common text

    Markup :  Common text

_Emphasized text_

    Markup :  _Emphasized text_ or *Emphasized text*

~~Strikethrough text~~

    Markup :  ~~Strikethrough text~~

**Strong text**

    Markup :  __Strong text__ or **Strong text**

**_Strong emphasized text_**

    Markup :  ___Strong emphasized text___ or ***Strong emphasized text***

[Named Link](http://www.google.fr/ "Named link title") and http://www.google.fr/ or <http://example.com/>

    Markup :  [Named Link](http://www.google.fr/ "Named link title") and http://www.google.fr/ or <http://example.com/>

[heading-1](#heading-1 "Goto heading-1")

    Markup: [heading-1](#heading-1 "Goto heading-1")

Table, like this one :

| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |

```
First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell
```

Adding a pipe `|` in a cell :

| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | \|            |

```
First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  |  \|
```

Left, right and center aligned table

| Left aligned Header | Right aligned Header | Center aligned Header |
| :------------------ | -------------------: | :-------------------: |
| Content Cell        |         Content Cell |     Content Cell      |
| Content Cell        |         Content Cell |     Content Cell      |

```
Left aligned Header | Right aligned Header | Center aligned Header
| :--- | ---: | :---:
Content Cell  | Content Cell | Content Cell
Content Cell  | Content Cell | Content Cell
```

`code()`

    Markup :  `code()`

```javascript
var specificLanguage_code = {
  data: {
    lookedUpPlatform: 1,
    query: "Kasabian+Test+Transmission",
    lookedUpItem: {
      name: "Test Transmission",
      artist: "Kasabian",
      album: "Kasabian",
      picture: null,
      link: "http://open.spotify.com/track/5jhJur5n4fasblLSCOcrTp",
    },
  },
};
```

    Markup : ```javascript
             ```

- Bullet list
  - Nested bullet
    - Sub-nested bullet etc
- Bullet list item 2

```
 Markup : * Bullet list
              * Nested bullet
                  * Sub-nested bullet etc
          * Bullet list item 2

-OR-

 Markup : - Bullet list
              - Nested bullet
                  - Sub-nested bullet etc
          - Bullet list item 2
```

1. A numbered list
   1. A nested numbered list
   2. Which is numbered
2. Which is numbered

```
 Markup : 1. A numbered list
              1. A nested numbered list
              2. Which is numbered
          2. Which is numbered
```

- [ ] An uncompleted task
- [x] A completed task

```
 Markup : - [ ] An uncompleted task
          - [x] A completed task
```

- [ ] An uncompleted task
  - [ ] A subtask

```
 Markup : - [ ] An uncompleted task
              - [ ] A subtask
```

> Blockquote
>
> > Nested blockquote

    Markup :  > Blockquote
              >> Nested Blockquote

_Horizontal line :_

---

    Markup :  - - - -

_Image with alt :_

![picture alt](http://via.placeholder.com/200x150 "Title is optional")

    Markup : ![picture alt](http://via.placeholder.com/200x150 "Title is optional")

Foldable text:

<details>
  <summary>Title 1</summary>
  <p>Content 1 Content 1 Content 1 Content 1 Content 1</p>
</details>
<details>
  <summary>Title 2</summary>
  <p>Content 2 Content 2 Content 2 Content 2 Content 2</p>
</details>

    Markup : <details>
               <summary>Title 1</summary>
               <p>Content 1 Content 1 Content 1 Content 1 Content 1</p>
             </details>

```html
<h3>HTML</h3>
<p>Some HTML code here</p>
```

Link to a specific part of the page:

[Go To TOP](#TOP)

    Markup : [text goes here](#section_name)
              section_title<a name="section_name"></a>

Hotkey:

<kbd>⌘F</kbd>

<kbd>⇧⌘F</kbd>

    Markup : <kbd>⌘F</kbd>

Hotkey list:

| Key       | Symbol |
| --------- | ------ |
| Option    | ⌥      |
| Control   | ⌃      |
| Command   | ⌘      |
| Shift     | ⇧      |
| Caps Lock | ⇪      |
| Tab       | ⇥      |
| Esc       | ⎋      |
| Power     | ⌽      |
| Return    | ↩      |
| Delete    | ⌫      |
| Up        | ↑      |
| Down      | ↓      |
| Left      | ←      |
| Right     | →      |

Emoji:

:exclamation: Use emoji icons to enhance text. :+1: Look up emoji codes at [emoji-cheat-sheet.com](http://emoji-cheat-sheet.com/)

    Markup : Code appears between colons :EMOJICODE:

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
