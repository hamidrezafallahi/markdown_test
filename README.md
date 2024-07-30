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
===================

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

## تنظیمات globalization

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

### و در نهایت برای استفاده از متن در یک صفحه به شکل زیر عمل میکنیم

```
import {useTranslations} from 'next-intl';

export default function HomePage() {

  const t = useTranslations('HomePage');    //نام صفحه ترجمه شده
    
    >├── message (1)
    │   ├── fa.json
    │   ├── en.json .

  return <h1>{t('title')}</h1>;         //انتخاب نام متن
    > {
  "HomePage": {    //نام صفحه مورد نظر
    "title": "Hello world!" // نام متن
  }
}
}
```





















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
