## Newsboat RSS Reader

### links

#### Newsboat links

1. https://newsboat.org/
2. https://github.com/newsboat/newsboat
3. https://newsboat.org/releases/2.24/docs/newsboat.html
4. https://wiki.archlinux.org/title/Newsboat

#### All about RSS

1. https://github.com/AboutRSS/ALL-about-RSS
2. https://github.com/plenaryapp/awesome-rss-feeds

### hacks

#### Способ подключеня к RSS
который позволяет подписаться на RSS, если владелец
ресурса специально спрятал атрибуты RSS, а сам канал оставил включенным.
Для того, чтобы подписаться на обновления такого ресурса, достаточно ввести в
адресной строке вашего браузера приставку `/feed` или `/rss.xml` или
`/?feed=rss`, к основной ссылке ресурса.

Пример ссылки: `http://www.site.com/feed`.

Если не сработало, то скорее всего канал RSS у этого ресурса выключен.

#### Obtaining web feeds

Even if a website does not advertise a web feed, it might still provide one.
Try appending `/feed` or `/rss` to the URL.
If that fails, open the website's source code by pressing `Ctrl+u`and then `Ctrl+f`
to search for
`<link rel="alternate" type="application/atom+xml"`
or
`<link rel="alternate" type="application/rss+xml"`.

The Firefox addon [Awesome RSS](https://addons.mozilla.org/firefox/addon/awesome-rss/) adds a clickable icon to the address bar if a web feed is available.

If a website does not provide a feed, try [RSS-Bridge](https://github.com/rss-bridge/rss-bridge).

---

[[/index|Get Back To Index]]
