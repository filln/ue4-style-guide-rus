
<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels / Maps

[Смотрите терминологию](0-ContentsAndDescription.md/#terms-level-map) относительно "levels" vs "maps".

### Sections

> 6.1 [Никаких ошибок или предупреждений](#levels-no-errors-or-warnings)

> 6.2 [Свет должен быть запечен](#levels-lighting-should-be-built)

> 6.3 [Никаких видимых Z-конфликтов (Z Fighting)](#evels-no-visible-z-fighting)

> 6.4 [Специфические правила для маркетплейса](#evels-levels-mp-rules)

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 Никаких ошибок или предупреждений 

Все уровни должны загружаться без ошибок и предупреждений. Если уровень загружается с любыми ошибками или предупреждениями, то они должны быть немедленно исправлены, чтобы предупредить накопление таких ошибок.
Вы можете запустить проверку открытого уровня в редакторе, используя консольную команду "map check".

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 Свет должен быть запечен 

Это нормально, когда во время разработки уровня иногда освещение еще не запечено. Но когда делается тестовый/внутренний/внешний или другой билд, освещение должно быть всегда запечено.

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 Никаких видимых Z-конфликтов (Z Fighting)

В уровне не должно быть видимых для игрока Z-конфликтов. [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) [Z-конфликт](https://ru.wikipedia.org/wiki/Z-буферизация)

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 Специфические правила для маркетплейса

Если проект будет выкладываться на маркетплейсе, то он должен следовать этим правилам.

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
### 6.4.1 Overview Level

Если ваш проект содержит ассеты, которые будут иметь визуализацию, то ваш проект должен иметь карту с названием "Overview".
Эта обзорная карта должна следовать правилам  [Epic's guidelines](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps).

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
### 6.4.2 Demo Level

Если ваш проект содержит ассеты, у которых есть демо-версия или есть какой-то туториал, то в проекте должна быть карта с названием "Demo". Этот уровень кроме прочего содержит документацию с некоторыми формами, которые иллюстрируют, как использовать ваш проект. Смотрите Epic's Content Examples project для примера. 
Если ваш проект является геймплейной механикой или другой системой, не принадлежащей к художественнным ассетам, то он тоже может иметь карту "Overview".
For example, `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Back to Top](#levels)**
