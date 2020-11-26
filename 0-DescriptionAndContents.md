
# Руководство по стилю проекта. 
# Содержание и описание.

<a name="toc"></a>
## Содержание
> 1. [Содержание и описание](/0-DescriptionAndContents.md)
> 1. [Соглашение о наименованиях](/1-AssetNamingConventions.md)
> 1. [Структура папок проекта](/2-DirectoryStructure.md)
> 1. [Блупринты](/3-Blueprints.md)
> 1. [Static Meshes](4-StaticMeshes.md)
> 1. [Particle Systems](5-ParticleSystems.md)
> 1. [Levels / Maps](6-LevelsMaps.md)
> 1. [Textures](7-Textures.md)

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

<a name="0.1"></a>
### 0.1 Если в вашем проекте UE4 уже используется руководство стиля, вы должны следовать ему

Если вы работаете над существующим проектом, или в команде, которая уже использует руководство стиля, вы должны ему (руководству) следовать. Во всех различиях между имеющимся и новым руководством стиля приоритет отдаётся имеющемуся.

Руководство по стилю, при этом, постоянно меняющийся документ, и рекомендуется предлагать вносить правки в ваше имеющееся руководство по стилю (и в этот документ), если это принесёт реальную пользу сообществу UE.

> #### "Споры по поводу стиля не имеют смысла. Должно быть руководство по стилю, а вы должны следовать ему".
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 Вся структура проекта, материалы для разработки, код в любом Unreal Engine 4 проекте должны выглядеть так, будто всё это создано одним человеком — не важно, как много людей на самом деле участвует

Смена проекта не должна требовать от вас переучиваться под новый стиль и структуру. Использование руководства по стилю избавит вас от гадания на кофейной гуще и неопределённости.

Также, руководство по стилю улучшает продуктивность создателей контента и управляемость проектом, т.к. каждому не требуется думать о стиле — достаточно просто воспользоваться руководством. Это руководство по стилю разрабатывается с учётом лучших практик, и его использование снизит частоту появления трудно отслеживаемых проблем.

<a name="0.3"></a>
### 0.3 Мы помогаем друзьям следовать хорошему стилю

Если вы видите, что кто-то работает не по вашему руководству стиля, или вовсе без какого-либо — объясните это тому человеку.

При работе в комаде и во время обсуждений в духе [Unreal Slackers (EN)](http://join.unrealslackers.org/) постоянство стиля также помогает быстро найти отклик на свою проблему. Никому не хочется рыться в макаронах блюпринтов и изучать непонятные названия материалов для разработки.

Если вы помогаете тому, кто следует другому, но постоянному и понятному руководству стиля, вы сможете к нему адаптироваться. Если вы увидили, что этот кто-то не следует какому-либо руководству стиля, отправьте ему ссылку на этот документ.

<a name="0.4"></a>
### 0.4 Команда без руководства стиля — не моя команда 

Одним из первых ваших вопросах при вступлении в команду разработчиков на UE4 должен быть "У вас есть руководство стиля?" Если его нет, то следует с подозрением относиться ко способности этих людей работать в команде.

##Источники
* [Оригинальная, английская версия](https://github.com/Allar/ue4-style-guide/README.md) by Allar
* [Russian Translation](https://github.com/CosmoMyzrailGorynych/ue4-style-guide-rus/blob/master/README.md) by CosmoMyzrailGorynych

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)