
<a name="ContentsAndDescription"></a>
# Руководство по стилю проекта. 
# Содержание и описание.

<a name="toc"></a>
## Содержание
> 0. [Содержание и описание](StyleGuide/0-ContentsAndDescription.md)
> 1. [Соглашение о наименованиях](StyleGuide/1-AssetNamingConventions.md)
> 2. [Структура папок проекта](StyleGuide/2-DirectoryStructure.md)
> 3. [Блупринты](StyleGuide/3-Blueprints.md)
> 4. [Static Meshes](StyleGuide/4-StaticMeshes.md)
> 5. [Particle Systems](StyleGuide/5-ParticleSystems.md)
> 6. [Levels / Maps](StyleGuide/6-LevelsMaps.md)
> 7. [Textures](StyleGuide/7-Textures.md)

*Наиболее разумный подход к Unreal Engine 4*

<a name="translations"></a>
##### Английские термины и их русификация (Levels/Maps)
_(От переводчика)_ Многие вещи будут называться в английском языке, но спокойно мешаться с русскими вариантами. Так, стайл-гайд — это руководство по стилю, ассет — материал для разработки.

## Основные термины

<a name="terms-level-map"></a>
##### Карты/Уровни (Levels/Maps)

Слово 'карта' в основном используется в обозначении слова 'уровень' — эти слова считаем взаимозаменяемыми. То же и с английскими Level и Map. О терминологии уровня смотрите [здесь (En)](https://en.wikipedia.org/wiki/Level_(video_gaming)) и [здесь (RU)](https://ru.wikipedia.org/wiki/%D0%A3%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C_(%D0%B8%D0%B3%D1%80%D1%8B)).

<a name="terms-cases"></a>
##### Использование верхнего и нижнего регистра
> ###### ДельфиСтиль
>
> Каждое слово начинается с большой буквы, а всё слово пишется без пробелов, нижних пробелов, дефисов и т.п. Например: `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.

<a name="terms-var-prop"></a>
##### Переменные / Свойства

Слова "переменная" и "свойство" в большинстве контекстов являются взаимозаменяемыми. Однако если они оба используются вместе в одном контексте:

<a name="terms-property"></a>
###### Свойство
Обычно относится к переменной, определенной в классе. Например, если `BP_Barrel` имела переменную `bExploded`, то `bExploded` можно назвать свойством `BP_Barrel`. 

Когда в контексте класса, часто используется, чтобы подразумевать доступ к ранее определенным данным.

<a name="terms-variable"></a>
###### Переменная
Обычно относится к переменной, определяемой как аргумент функции или локальная переменная внутри функции.

Когда в контексте класса, часто используется для обсуждения о его определении и о том, что оно будет содержать.

<a name="0.1"></a>
### 0.1 Если в вашем проекте UE4 уже используется руководство стиля, вы должны следовать ему

Если вы работаете над существующим проектом, или в команде, которая уже использует руководство стиля, вы должны ему (руководству) следовать.

Руководство по стилю, при этом, постоянно меняющийся документ.

> #### "Споры по поводу стиля не имеют смысла. Должно быть руководство по стилю, а вы должны следовать ему".
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 Вся структура проекта, материалы для разработки, код в любом Unreal Engine 4 проекте должны выглядеть так, будто всё это создано одним человеком — не важно, как много людей на самом деле участвует

Смена проекта не должна требовать от вас переучиваться под новый стиль и структуру. Использование руководства по стилю избавит вас от гадания на кофейной гуще и неопределённости.

Также, руководство по стилю улучшает продуктивность создателей контента и управляемость проектом, т.к. каждому не требуется думать о стиле — достаточно просто воспользоваться руководством. Это руководство по стилю разрабатывается с учётом лучших практик, и его использование снизит частоту появления трудно отслеживаемых проблем.

<a name="0.3"></a>
### 0.3 Мы помогаем друзьям следовать хорошему стилю

Если вы видите, что кто-то работает не по текущему руководству стиля — объясните это тому человеку.

При работе в комаде и во время обсуждений постоянство стиля также помогает быстро найти отклик на свою проблему. Никому не хочется рыться в макаронах блюпринтов и изучать непонятные названия материалов для разработки.

## Источники
* [Оригинальная, английская версия](https://github.com/Allar/ue4-style-guide/blob/master/README.md) by Allar
* [Russian Translation](https://github.com/CosmoMyzrailGorynych/ue4-style-guide-rus/blob/master/README.md) by CosmoMyzrailGorynych

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](StyleGuide/LICENSE)

**[⬆ Back to Top](#ContentsAndDescription)**