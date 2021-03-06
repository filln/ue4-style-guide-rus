<a name="AssetNamingConventions"></a>
<a name="1"></a>
## 1. Соглашение о наименованиях 

Соглашение о наименованиях должно восприниматься как закон. В проекте, следующем соглашению о наименованиях, легко управлять ассетами, искать и обрабатывать их.

В большинстве случаев, ассетам присваивается префикс-аббревиатура на основе названия типа этого ассета + нижний пробел `_`.

<a name="prohibited-languages"></a>
<a name="1.0"></a>
### 1.0 Русский и иные языки (от переводчика)
Использование русских и иных языков в названиях ассетов строго запрещается. Нет ничего хуже, чем пытаться понять проект с французскими названиями, когда вы не владеете таким языком. Точно так же будет плохо зарубежным друзьям при разборе вашего проекта.

Такие проекты нельзя будет передавать лицам из других стран, когда вам потребуется помощь. Также, не-латинские символы могут вызвать ошибки при компиляции, преобразовании и в ходе других внутренних процессов UE4 и сторонних плагинов — такие ошибки будет трудно отловить и исправить, так что лучше не делайте их вообще.

*Не бойтесь пользоваться переводчиком*. Лучше чудаковатое название на английском, нежели написанное транслитом слово `Pchela`, или, того хуже, так и оставленное на русском `Пчела`.

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 Базовое название - `Префик_БазовоеНазвание_Вариант_Суффикс` 

У каждого ассета должно быть своё _базовое название_. Оно используется как средство логической группировки материалов разработки. Любой ассет, являющийся частью определённой логической группы, должен следовать стандарту  `Префик_БазовоеНазвание_Вариация_Суффикс`.

Использование схемы `Префик_БазовоеНазвание_Вариация_Суффикс` с её осознанием уже гарантирует создание "хороших" имён. Вот подробные правила по использованию этой схемы:

* `Префикс` и `Суффикс` определяется типом ассета, исходя из таблиц [Модификаторов имён ассетов](#asset-name-modifiers).
* `Базовое название` определяется коротким и легко отличимым названием касательно предметной области вашей группы ассетов. Например, если у вас есть персонаж Вася, то все ассеты Васи должны содержать `БазовоеНазвание` = `Vasya`.
* Для особенных или уникальных вариантов ассета используйте `Вариант` — короткое и легко различимое имя, отражающее логическую группировку ассетов, образующих подмножество на основе базового имя ассета. Например, если у Васи есть несколько скинов, то у этих скинов должно быть всё то же базовое имя `Vasya`, но также и `Вариант`. "Злой" скин можно назвать `Vasya_Evil`, а скин "Ретро"— `Vasya_Retro`.
* Для уникальных но схожих ассетов, относящихся к одной группе, добавляется нумерующий `Вариант` — двузначное число, нумерация которого начинается с `01`. Например, если ваш художник окружения генерирует валуны, которые нельзя просто так взять и назвать, то их можно назвать как `Rock_01`, `Rock_02`, `Rock_03`, и т.д. За исключением редких случаев, не используйте трёхзначное число. Если у вас более 100 ассетов в одной группе, вам следует разбить её на несколько других, используя другие базовые названия или варианты.
* В зависимости от того, как у вас создаются ассеты, вы можете использовать несколько имён-вариантов, друг за другом. Например, если вы создаёте ассеты для пола, вам будет нужно использовать базовое имя `Flooring` с вариантами вроде `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

<a name="1.1-examples"></a>
#### 1.1 Примеры

##### 1.1e1 Вася

| Тип ассета (RU)          |Тип ассета (EN)           | Название ассета                |
| ------------------------ | ------------------------ | ------------------------------ |
| Скелетный меш            | Skeletal Mesh            | SK_Bob                         |
| Материал                 | Material                 | M_Bob                          |
| Текстура (Diffuse/Albedo)| Texture (Diffuse/Albedo) | T_Bob_D                        |
| Текстура (Normal)        | Texture (Normal)         | T_Bob_N                        |
| Текстура (Злой Diffuse)  | Texture (Злой Diffuse)   | T_Bob_Evil_D                   |

##### 1.1e2 Валуны

| Тип ассета (RU)           | Тип ассета (EN)         | Название ассета                |
| ------------------------- | ----------------------- | ------------------------------ |
| Статичный меш (01)        | Static Mesh (01)        | S_Rock_01                      |
| Статичный меш (02)        | Static Mesh (02)        | S_Rock_02                      |
| Статичный меш (03)        | Static Mesh (03)        | S_Rock_03                      |
| Материал                  | Material                | M_Rock                         |
| Экземпляр материала (Снег)| Material Instance (Snow)| MI_Rock_Snow                   |

### 1.2 Модификаторы имён ассетов

Используйте эти таблицы наряду с [базовым названием](#base-asset-name), когда именуете ассеты.

#### Подразделы

> 1.2.1 [Часто используемые](#anc-common)

> 1.2.2 [Анимация](#anc-animations)

> 1.2.3 [Искусственный интеллект](#anc-ai)

> 1.2.4 [Блупринты](#anc-bp)

> 1.2.5 [Материалы](#anc-materials)

> 1.2.6 [Текстуры](#anc-textures)

> 1.2.7 [Разное](#anc-misc)

> 1.2.8 [Paper 2D](#anc-paper2d)

> 1.2.9 [Физика](#anc-physics)

> 1.2.10 [Звуки](#anc-sound)

> 1.2.11 [Графический интерфейс пользователя](#anc-ui)

> 1.2.12 [Эффекты](#anc-effects)

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Часто используемые 

| Тип ассета (RU)      | Тип ассета (EN)    | Префикс      | Суффикс    | Примечания                          |
| -------------------- | ------------------ | ------------ | ---------- | ----------------------------------- |
| Карта / уровень      | Level / Map        |              |            | [Должны быть в папке `Maps`.](#2.3) |
| Уровень (постоянный) | Level (Persistent) |              | _P         |                                     |
| Уровень (аудио)      | Level (Audio)      |              | _Audio     |                                     |
| Уровень (освещение)  | Level (Lighting)   |              | _Lighting  |                                     |
| Уровень (геометрия)  | Level (Geometry)   |              | _Geo       |                                     |
| Уровень (геймплей)   | Level (Gameplay)   |              | _Gameplay  |                                     |
| Блупринт             | Blueprint          | BP_          |            |                                     |
| Материал             | Material           | M_           |            |                                     |
| Статичный меш        | Static Mesh        | SM_          |            |                                     |
| Скелетный меш        | Skeletal Mesh      | SK_          |            |                                     |
| Текстура             | Texture            | T_           | _?         | См. [Текстуры](#anc-textures)       |
| Система частиц       | Particle System    | PS_          |            |                                     |
| Виджет-блупринт      | Widget Blueprint   | WBP_         |            |                                     |

<a name="anc-ai"></a>
<a name="1.2.2"></a>
### 1.2.2 Искусственный интеллект 

| Тип ассета (RU)         | Тип ассета (EN)   | Префикс      | Суффикс    | Примечания |
| ----------------------- | ----------------- | ------------ | ---------- | ---------- |
| ИИ контроллер           | AI Controller     | AIC_         |            |            |
| Дерево поведений        | Behavior Tree     | BT_          |            |            |
| Доска состояний         | Blackboard        | BB_          |            |            |
| Декторатор              | Decorator         | BTDecorator_ |            |            |
| Сервис                  | Service           | BTService_   |            |            |
| Задание                 | Task              | BTTask_      |            |            |
| Система запросов среды  | Environment Query | EQS_         |            |            |
| Контекст системы запросов среды | EnvQueryContext   | EQS_ | Context    |            |

<a name="anc-animations"></a>
<a name="1.2.3"></a>
#### 1.2.3 Анимация 

| Тип ассета (RU)             | Тип ассета (EN)       | Префикс    | Суффикс    | Примечания               |
| --------------------------- | --------------------- | ---------- | ---------- | ------------------------ |
| Сдвиг прицела               | Aim Offset            | AO_        |            |                          |
| Сдвиг прицела 1D            | Aim Offset 1D         | AO_        |            |                          |
| Блюпринт анимации           | Animation Blueprint   | ABP_       |            |                          |
| Композиция анимации         | Animation Composite   | AC_        |            |                          |
| Монтаж анимации             | Animation Montage     | AM_        |            |                          |
| Последовательность анимаций | Animation Sequence    | AS_        |            |                          |
| Пространство смешивания     | Blend Space           | BS_        |            |                          |
| Пространство смешивания 1D  | Blend Space 1D        | BS_        |            |                          |
| Последовательность уровня   | Level Sequence        | LS_        |            |                          |
| Точка смешивания            | Morph Target          | MT_        |            |                          |
| Риг                         | Rig                   | Rig_       |            |                          |
| Анимация камеры             | Camera Animation Sequence | CA_        |            |                          |

<a name="anc-bp"></a>
<a name="1.2.4"></a>
### 1.2.4 Блупринты 

| Тип ассета (RU)             | Тип ассета (EN)            | Префикс       | Суффикс | Примечания                       |
| --------------------------- | -------------------------- | ------------- | ------- | -------------------------------- |
| Блупринт                    | Blueprint                  | BP_           |         |                                  |
| Библиотека блупринт-функций | Blueprint Function Library | BPFL_         |         |                                  |
| Блупринт-интерфейс          | Blueprint Interface        | BPI_          |         |                                  |
| Библиотека бупринт-макросов | Blueprint Macro Library    | BPML_         |         | По возможности не используйте библиотеки макросов вообще |

<a name="anc-data"></a>
<a name="1.2.5"></a>
### 1.2.5 Данные 

| Тип ассета (RU)             | Тип ассета (EN)            | Префикс    | Суффикс    | Примечания                       |
| --------------------------- | -------------------------- | ---------- | ---------- | -------------------------------- |
| Перечисление                | Enumeration                | E          |            | Без нижнего пробела              |
| Структура                   | Structure                  | S          |            | Без нижнего пробела              |
| Цветовая кривая             | Color Curve                | Curve_     | _Color     |                                  |
| Табличная кривая            | Curve Table                | Curve_     | _Table     |                                  |
| Вещественная кривая         | Float Curve                | Curve_     | _Float     |                                  |
| Векторная кривая            | Vector Curve               | Curve_     | _Vector    |                                  |
| Набор данных                | Data Asset                 | *_         | _DataAsset | Префикс основывается на классе   |
| Таблица данных              | Data Table                 | DT_        |            |                                  |
| Строковая таблица           | String Table               | ST_        |            |                                  |
| Данные Matinee              | Matinee Data               | Matinee_   |            |                                  |

<a name="anc-maps"></a>
<a name="1.2.6"></a>
### 1.2.6 Уровень 

| Тип ассета (RU)             | Тип ассета (EN)    | Префикс       | Суффикс    | Примечания                          |
| --------------------------- | -------------------| ------------- | ---------- | ----------------------------------- |
| Карта / уровень             | Level / Map        |               |            | [Должны быть в папке `Maps`.](#2.3) |
| Уровень (постоянный)        | Level (Persistent) |               | _P         |                                     |
| Уровень (аудио)             | Level (Audio)      |               | _Audio     |                                     |
| Уровень (освещение)         | Level (Lighting)   |               | _Lighting  |                                     |
| Уровень (геометрия)         | Level (Geometry)   |               | _Geo       |                                     |
| Уровень (геймплей)          | Level (Gameplay)   |               | _Gameplay  |                                     |

<a name="anc-landscape"></a>
<a name="1.2.7"></a>
### 1.2.7 Ландшафт 

| Тип ассета (RU)             | Тип ассета (EN)         | Префикс    | Суффикс    | Примечания                          |
| --------------------------- | ------------------------| ---------- | ---------- | ----------------------------------- |
| Тип растительности          | Foliage Type            | FT_        |            |                                  |
| Тип растительности          | Landscape Grass Type    | LG_        |            |                                  |
| Слой ландшафта              | Landscape Layer         | LL_        |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.8"></a>
### 1.2.8 Материалы 

| Тип ассета (RU)               | Тип ассета (En)               | Префикс      | Суффикс | Примечания                |
| ----------------------------- | ----------------------------- | ------------ | ------- | ------------------------- |
| Материал                      | Material                      | M_           |         |                           |
| Материал пост-обработки       | Material (Post Process)       | PP_          |         |                           |
| Функция материалов            | Material Function             | MF_          |         |                           |
| Экземпляр материала           | Material Instance             | MI_          |         |                           |
| Материал Parameter Collection | Material Parameter Collection | MPC_         |         |                           |
| Профиль подповерхности        | Subsurface Profile            | SSP_         |         |                           |
| Материал для частиц           | Material (for Particle System)| M_, MI_      | _Decal  |                           |

<a name="anc-meshes"></a>
<a name="1.2.9"></a>
#### 1.2.9 Меши
| Тип ассета (RU)             | Тип ассета (EN)       | Префикс    | Суффикс    | Примечания               |
| --------------------------- | --------------------- | ---------- | ---------- | ------------------------ |
| Скелетный меш               | Skeletal Mesh         | SK_        |            |                          |
| Скелет                      | Skeleton              | SKEL_      |            |                          |
| Разрушаемый меш             | Destructible Mesh     | DM_        |            |                          |

<a name="anc-particles"></a>
<a name="1.2.10"></a>
#### 1.2.10 Частицы
| Тип ассета (RU)             | Тип ассета (EN)       | Префикс    | Суффикс    | Примечания               |
| --------------------------- | --------------------- | ---------- | ---------- | ------------------------ |
| Система частиц              | Particle System       | PS_        |            |                          |

<a name="anc-physics"></a>
<a name="1.2.11"></a>
### 1.2.11 Физика

| Тип ассета (RU)         | Тип ассета (EN)         | Префикс    | Суффикс    | Примечания                       |
| ----------------------- | ----------------------- | ---------- | ---------- | -------------------------------- |
| Физический материал     | Physical Material       | PM_        |            |                                  |
| Физический ассет        | Physical Asset          | PHYS_      |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.12"></a>
### 1.2.12 Звуки

| Тип ассета (RU)         | Тип ассета (EN)         | Префикс    | Суффикс    | Примечания                       |
| ----------------------- | ----------------------- | ---------- | ---------- | -------------------------------- |
| Голос диалога           | Dialogue Voice          | DV_        |            |                                  |
| Запись диалога          | Dialogue Wave           | DW_        |            |                                  |
| Звукозапись медиа       | Media Sound Wave        | MSW_       |            |                                  |
| Эффект ревербации       | Reverb Effect           | Reverb_    |            |                                  |
| Затухание звука         | Sound Attenuation       | ATT_       |            |                                  |
| Класс звука             | Sound Class             |            |            | Без префиксов/суффиксов. Должен быть в отдельной папке `SoundClasses` |
| Очерёдность звуков      | Sound Concurrency       |            | _SC        | Должен быть назван на основе `SoundClass` |
| Композиция звуков       | Sound Cue               | A_         | _Cue       |                                  |
| Микс звуков             | Sound Mix               | Mix_       |            |                                  |
| Звукозапись             | Sound Wave              | A_         |            |                                  |

<a name="anc-textures"></a>
<a name="1.2.13"></a>
### 1.2.13 Текстуры 

| Тип ассета (RU)                  | Тип ассета (EN)             | Префикс      | Суффикс    | Примечания                       |
| -------------------------------- | --------------------------- | ------------ | ---------- | -------------------------------- |
| Текстура                         | Texture                     | T_           |            |                                  |
| Текстура (Diffuse/Альбедо/Основной цвет)| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Текстура (Нормаль)               | Texture (Normal)            | T_           | _N         |                                  |
| Текстура (Грубость)              | Texture (Roughness)         | T_           | _R         |                                  |
| Текстура (Alpha/Прозрачность)    | Texture (Alpha/Opacity)     | T_           | _A         |                                  |
| Текстура (Нейтральный свет)      | Texture (Ambient Occlusion) | T_           | _AO        |                                  |
| Текстура (Неровность)            | Texture (Bump)              | T_           | _B         |                                  |
| Текстура (Излучение)             | Texture (Emissive)          | T_           | _E         |                                  |
| Текстура (Маска)                 | Texture (Mask)              | T_           | _M         |                                  |
| Текстура (Блеск)                 | Texture (Specular)          | T_           | _S         |                                  |
| Текстура (упакованная)           | Texture (Packed)            | T_           | _*         | См. примечание об [упаковке текстур](#anc-textures-packing). |
| Текстура-куб                     | Texture Cube                | TC_          |            |                                  |
| Текстура-медиа                   | Media Texture               | MT_          |            |                                  |
| Область прорисовки               | Render Target               | RTT_         |            |                                  |
| Область прорисовки текстуры-куба | Cube Render Target          | RTC_         |            |                                  |
| Профиль освещения                | Texture Light Profile       | TLP          |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.13.1"></a>
#### 1.2.13.1 Упаковка текстур 
Упаковка сразу нескольких слоёв информации в одну текстуру — стандартная практика. Примером служит упаковка текстур Emissive, Roughness, Ambient Occlusion как красный, зелёный и синий каналы одной текстуры. Чтобы построить суффикс для таких текстур, просто последовательно запишите суффиксы отдельных масок из таблицы выше, напр. `_ERO`.

> Часто альфа-канал включают в карту Diffuse/Альбедо. Так как это стандартная практика, добавлять суффикс `A` в суффикс `_D` необязательно.

Упаковывать сразу 4 канала информации в одну текстуру (в RGBA) не рекомендуется, за исключением использования канала A как Alpha вместе с картой Diffuse/Альбедо.

<a name="anc-ui"></a>
<a name="1.2.14"></a>
### 1.2.14 Графический интерфейс пользователя

| Тип ассета (RU)         | Тип ассета (EN)         | Префикс      | Суффикс    | Примечания                       |
| ----------------------- | ----------------------- | ------------ | ---------- | -------------------------------- |
| Шрифт                   | Font                    | Font_        |            |                                  |
| Кисть Slate             | Slate Brush             | Brush_       |            |                                  |
| Стиль виджета Slate     | Slate Widget Style      | Style_       |            |                                  |
| Виджет-блупринт         | Widget Blueprint        | WBP_         |            |                                  |

<a name="anc-misc"></a>
<a name="1.2.15"></a>
### 1.2.15 Разное

| Тип ассета (RU)         | Тип ассета (EN)         | Префикс    | Суффикс    | Примечания                       |
| ----------------------- | ----------------------- | ---------- | ---------- | -------------------------------- |
| Эффект физического отклика| Force Feedback Effect | FFE_       |            |                                  |
| Медиапроигрыватель      | Media Player            | MP_        |            |                                  |
| Библиотека объектов     | Object Library          | OL_        |            |                                  |
| Перенаправление         | Redirector              |            |            | Перенаправление должно быть исправлено при первой возможности |

**[⬆ Back to Top](#AssetNamingConventions)**
