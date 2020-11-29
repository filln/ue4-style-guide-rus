
## 3. Блупринты 

Этот раздел направлен на блупринты и их внутреннее обустройство. Где возможно, эти правила подчиняются [стандарту кодинга Epic](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

### Подразделы

> 3.1 [Компиляция](#bp-compiling)

> 3.2 [Переменные](#bp-vars)

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Компиляция 

Все блупринты должны компилиться без предупреждений и ошибок. Вы должны исправить все предупреждения и ошибки при первой возможности, т.к. они сразу могут превратиться в снежный ком проблем и вызвать непредвиденное поведение.

*Никогда не отправляйте* (submit) сломанные блупринты в систему контроля версиями. Если вам нужно хранить их в системе контроля версий, отложите их (shelve).

Сломанные блупринты могут вызвать массу проблем — таких, как поломанные связи, некорректное поведение, падения при сборке, частые ненужные перекомпиляции. Один сломанный блупринт способен порушить всю вашу игру.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Переменные

#### Подразделы

> 3.2.1 [Именование](#bp-vars)

> 3.2.2 [`Editable`](#bp-vars-editable)

> 3.2.3 [Категории](#bp-vars-categories)

> 3.2.4 [Уровни доступа](#bp-vars-access)

> 3.2.5 [`Advanced`](#bp-vars-advanced)

> 3.2.6 [`Transient`](#bp-vars-transient)

> 3.2.7 [`SaveGame`](#bp-vars-savegame)

> 3.2.8 [Переменные `Config`](#bp-vars-config)

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Именование 

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 Существительные 

Все не-булевые переменные должны быть чёткими, недвусмысленными, описательными существительными.

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 ДельфиСтиль 

Все не-булевые переменные должны быть написаны в [ДельфиСтиле](/0-ContentsAndDescription.md#terms-cases).

<a name="3.2.1.2e"></a>
###### 3.2.1.2e Примеры:

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3 Префикс `b` для булевых переменных 

Все булевы значения должны следовать ДельфиСтилю, но иметь префикс в виде малой `b`.

Например: `bDead` и `bEvil`, **но не** `Dead` и `Evil`.

Редактор блупринтов в UE4 распознаёт эту `b` и не выводит её при выводе удобочитаемого текста.

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 Имена булевых значений 

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1 Общая информация и независимые состояния 

Все булевые переменные должны быть качественными прилагательными. Не включайте вопросительные слова, например, `Is`. Такие слова зарезервированы для функций.

Например: используйте `bDead` и `bHostile`, но **не** `bIsDead` и `bIsHostile`.

Старайтесь также не использовать в названиях глаголы (напр. `bRunning`). Глаголы, как правило, ведут к сложным состояниям.

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 Сложные состояния 

Не используйте булевы переменные для описания сложных и/или зависимых состояний. Это приводит к затруднённому управлению этих состояний и нечитабельности. Вместо этого используйте перечисление (Enum).

Например: описывая пушку, **не используйте** `bReloading` и `bEquipping`, если пушка не может одновременно заряжаться и быть в процессе экипировки. Обозначьте перечисление `EWeaponState` и используйте вместо булевых переменных одну переменную `WeaponState` соответствующего типа. Так добавлять новые состояния пушке будет проще.

Пример: **не используйте** `bRunning` ("Бежит"), если вам также нужны `bWalking` ("Ходит") и `bSprinting` ("Спринтует", кратковременное ускорение). Вам нужно перечисление с чёткими названиями вариантов.

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Предметная область переменной определяется самим блупринтом, но не названием 

Все названия переменных не должны быть избыточны и упоминать свой контекст, так как все переменные из блупринта уже обладают своим контекстом.

<a name="3.2.1.5e"></a>
###### 3.2.1.5e Пример:

Пусть у нас есть блупринт `BP_PlayerCharacter`.

**Нельзя**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

Названия этих переменных избыточны. Если переменные описаны в `BP_PlayerCharacter`, то это значит, что они характеризуют именно `BP_PlayerCharacter`.

**Надо**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6 _Не включайте_ названия атомарных типов 

Атомарные, или примитивные, переменные — это такие переменные, что описывают своё значение в простейшей форме — напимер, в виде булевого значения, целочисленного, вещественного, перечисления (Enum).

Строки (именно String, не Text!), Rotator и векторы тоже считаются атомарными в блупринтах и тоже не должны включать названия типа в своих именах. Тем не менее, с технической точки зрения они не являются атомарными.

> Хоть вектора и состоят каждый из трёх вещественных значений, с векторами часто работают как с единым целым. То же и с Rotator.

> _Нельзя_ считать Text атомарным типом, т.к. они включают в себе скрытый функционал по локализации. Атомным типом является `String`, но не `Text`.

Атомные переменные не должны включать название типа переменной в своём названии.

Например: используйте `Score`, `Kills` и `Description`, **но не** `ScoreFloat`, `FloatKills`, `DescriptionString`.

Единственное исключение этого правила — когда имеется ввиду "количество того-то" **и** когда использование имени без типа переменной приводит к затруднению чтения.

Например: генератор забора создаёт X досок. Это X нужно сохранить в переменной `NumBoards` или `BoardsCount`, но не `Boards`, т.к. `Boards` может уже относиться к массиву переменных типа `Board`.

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 **Нужно** включать имена неатомарных типов в названиях переменных 

Неатомартные, или сложные, переменные — это такие, что отражают свою информацию как набор атомарных переменных. Структуры, классы, интерфейсы, примитивы со скрытым поведением (вроде `Text` и `Name`) попадают под это правило.

> В то время, как массив атомарных значений — это список атомарных переменных, массивы не меняют "атомарность" типа переменных.

Эти переменные должны включать названия их типов, но также и подразумевать контекст использования.

Если класс _владеет_ экземпляром сложной переменной, напр. если у `BP_PlayerCharacter` есть `BP_Hat`, то она должна называться как тип переменной, без каких-либо изменений.

Например: используйте `BP_Hat`, `BP_Flag`, и `BP_Ability`, **но не** `MyHat`, `MyFlag`, или `PlayerAbility`.

Если класс _не владеет_ значением сложной переменной, то нужно использовать существительное вместе с названием типа переменной.

Например: если у `BP_Turret` есть способность нацеливаться на `BP_PlayerCharacter`, она (туррель) должна хранить переменную `TargetPlayer` — так в контексте `BP_Turret` будет понятно, что это ссылка на другую переменную сложного типа, которой туррель не владеет.


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Массивы 

Массивы подчиняются правилам выше, но описываются во множественном числе.

Например: используйте `Targets`, `Hats` и `EnemyPlayers`, **но не** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Редактируемые (`Editable`) переменные 

Все переменные, которые спокойно можно менять с целью настройки поведения блупринта, должны быть отмечены как  `Editable`.

Аналогично, все те переменные, которые небезопасно редактировать и которые не должны быть раскрыты дизайнерам, не должны быть отмечены как `Editable`, за исключением тех случаев, когда переменная требует флага `Expose On Spawn`.

Не помечайте переменные флагом `Editable` произвольным образом.

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 Подсказки 

Все переменные типа `Editable`, включая те, что были помечены так только из-за флага `Expose On Spawn`, должны иметь своё описание в поле `Tooltip`, которое должно показывать, как изменение этого значения меняет поведение блупринта.

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
##### 3.2.2.2 Слайдеры и пределы допустимых значений 

Все переменные с флагом `Editable` должны использовать слайдеры (Slider) и пределы допустимых значений (Value Range), если есть хоть какое-нибудь значение, которое _не должно_ использоваться.

Пример: блупринт, генерирующий забор, может иметь редактируемую переменную `BoardsCount`, и значение -1 не будет являться для него рабочим. Используйте пределы допустимых значений, чтобы обозначить 0 как минимальное значение.

Если редактируемая переменная используется в Construction Script, у неё должен быть настроенный слайдер (Slider Range), который препятствует назначению таких значений, что могут обрушить редактор.

Пределы допустимых значений нужно устанавливать только тогда, когда известны границы этих значений. Если слайдер предотвращает случайный ввод слишком больших значений, то неустановленное значение пределов всё же позволяет указать значения вне диапазона слайдера — "опасные", но всё ещё валидные.

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Категории 

Если у класса совсем немного переменных, то использование категорий не требуется.

Если у класса есть некоторое количество переменных (5-10), все переменные с флагом `Editable` должны обладать своей нестандартной категорией. Для общих переменных создаётся категория `Config`.

Если у класса большое количество переменных, то все переменные с флагом `Editable` должны быть помещены в подкатегории внутри `Config`. Нередактируемые переменные (без флага `Editable`) должны быть помещены в отдельные категории с понятными названиями.

> Вы можете создавать подкатегории, используя символ вертикальной черты `|`, напр. `Config | Animations`.

Пример: набор переменных оружия может быть расположен в следующей иерархии:

    |-- Config
    |   |-- Animations
    |   |-- Effects
    |   |-- Audio
    |   |-- Recoil
    |   |-- Timings
    |-- Animations
    |-- State
    |-- Visuals

<a name="3.2.4"></a>
<a name="bp-vars-access"></a>
#### 3.2.4 Уровень доступа переменных 

В C++ есть реализация уровня доступа переменных. Уровень доступа `Public` означает, что все экземпляры любых классов могут получить доступ к этой переменной. Переменные `Protected` могут использованы только самим классом и дочерними классами. `Private` значит, что только сам класс может видеть эти переменные (дочерние не видят).

В блупринтах, по крайней мере — на данный момент —, нет реализации уровня доступа переменных.

Считайте переменные с флагом `Editable` как публичные. Переменные без этого флага считайте как `Protected`.

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 Закрытые (`Private`) переменные 

В том случае, если не известно, должна ли быть переменная доступна только в самом классе, но не в дочерних, не отмечайте переменную как `Private`. Используйте `Protected` и закрывайте переменную только тогда, когда вы абсолютно уверены, что хотите ограничить использование переменных в дочерних классах.

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 `Advanced Display` 

Если переменная должна быть редактируема, но, в большинстве случаев, нетронута, отметьте её флагом `Advanced Display`. Переменная будет скрыта, но может быть отображена по клику стрелки в конце категории.

Сам флаг `Advanced Display` тоже является скрытым за этой стрелкой на панеле `Details`.

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 `Transient`

Все переменные без флага `Editable` и которые должны обладать нулевым начальным значением, должны быть помечены как `Transient`.

Такие переменные не требуют сохранения и загрузки их значения и изначально равны нулю (zero или null). Они полезны для тех случаев, когда требуется ссылка на других объектов и актёров, не известная до запуска игры.

Этот флаг предотвращает сохранение ссылки на эту переменную внутри редактора и ускоряет процесс сохранения и загрузки класса.

<a name="3.2.7"></a>
<a name="bp-vars-savegame"></a>
#### 3.2.7 Переменные с флагом `SaveGame` 

Используйте флаг `SaveGame` только для переменных класса, унаследованного от класса `SaveGame`. Отмечайте этот флаг, только если `SaveGame` должен сохранить значение. Временные переменные, не хранимые в слоте сохранения, не должны отмечаться этим флагом.

Не смешивайте `SaveGame` и `Transient` — это бесполезно.

<a name="3.2.8"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 Флаг `Config Variable` 

Не используйте флаг `Config Variable`. Дизайнерам будет труднее из-за этого контроллировать поведение блупринта. Этот флаг используется только в C++ для редко меняющихся значений, как если бы они были под двойным флагом `Advanced Display`.

### 3.3 Functions, Events, and Event Dispatchers 

This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Function Naming 

The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Is it a pure function?
* Is it fetching state information?
* Is it a handler?
* Is it an RPC?
* What is its purpose?

These questions and more can all be answered when functions are named appropriately.

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 All Functions Should Be Verbs 

All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should all start with verbs. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

`OnRep` functions, event handlers, and event dispatchers are an exception to this rule.

Good examples:

* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `Jump` - Good example if in a Character class, otherwise, needs context.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:

* `Dead` - Is Dead? Will deaden?
* `Rock`
* `ProcessData` - Ambiguous, these words mean nothing.
* `PlayerState` - Nouns are ambiguous.
* `Color` - Verb with no context, or ambiguous noun.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`

All functions for replicated with notification variables should have the form `OnRep_Variable`. This is forced by the Blueprint editor. If you are writing a C++ `OnRep` function however, it should also follow this convention when exposing it to Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Info Functions Returning Bool Should Ask Questions 

When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow [the verb rule](#bp-funcs-naming-verbs).

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

Good examples:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" is past-tense of "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" when referring to 'previous frame' or 'previous state'.
* `CanReload` - ["Can" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Bad examples:

* `Fire` - Is on fire? Will fire? Do fire?
* `OnFire` - Can be confused with event dispatcher for firing.
* `Dead` - Is dead? Will deaden?
* `Visibility` - Is visible? Set visibility? A description of flying conditions?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers and Dispatchers Should Start With `On` 

Any function that handles an event or dispatches an event should start with `On` and continue to follow [the verb rule](#bp-funcs-naming-verbs). The verb may move to the end however if past-tense reads better.

[Collocations](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) of the word `On` are exempt from following the verb rule.

`Handle` is not allowed. It is 'Unreal' to use `On` instead of `Handle`, while other frameworks may prefer to use `Handle` instead of `On`.

Good examples:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Bad examples:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target 

Any time an RPC is created, it should be prefixed with either `Server`, `Client`, or `Multicast`. No exceptions.

After the prefix, follow all other rules regarding function naming.

Good examples:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Bad examples:

* `FireWeapon` - Does not indicate its an RPC of some kind.
* `ServerClientBroadcast` - Confusing.
* `AllNotifyDeath` - Use `Multicast`, never `All`.
* `ClientWeapon` - No verb, ambiguous.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 All Functions Must Have Return Nodes 

All functions must have return nodes, no exceptions.

Return nodes explicitly note that a function has finished its execution. In a world where blueprints can be filled with `Sequence`, `ForLoopWithBreak`, and backwards reroute nodes, explicit execution flow is important for readability, maintenance, and easier debugging.

The Blueprint compiler is able to follow the flow of execution and will warn you if there is a branch of your code with an unhandled return or bad flow if you use return nodes.

In situations like where a programmer may add a pin to a Sequence node or add logic after a for loop completes but the loop iteration might return early, this can often result in an accidental error in code flow. The warnings the Blueprint compiler will alert everyone of these issues immediately.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 No Function Should Have More Than 50 Nodes 

Simply, no function should have more than 50 nodes. Any function this big should be broken down into smaller functions for readability and ease of maintenance.

The following nodes are not counted as they are deemed to not increase function complexity:

* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 All Public Functions Should Have A Description 

This rule applies more to public facing or marketplace blueprints, so that others can more easily navigate and consume your blueprint API.

Simply, any function that has an access specificer of Public should have its description filled out. 

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name 

If your project includes a plugin that defines `static` `BlueprintCallable` functions, they should have their category set to the plugin's name or a subset category of the plugin's name.

For example, `Zed Camera Interface` or `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs 

This section covers things that apply to all Blueprint graphs.

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 No Spaghetti 

Wires should have clear beginnings and ends. You should never have to mentally untangle wires to make sense of a graph. Many of the following sections are dedicated to reducing spaghetti.

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Align Wires Not Nodes 

Always align wires, not nodes. You can't always control the size and pin location on a node, but you can always control the location of a node and thus control the wires. Straight wires provide clear linear flow. Wiggly wires wear wits wickedly. You can straighten wires by using the Straighten Connections command with BP nodes selected. Hotkey: Q

Good example: The tops of the nodes are staggered to keep a perfectly straight white exec line.
![Aligned By Wires](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-good.png "Aligned By Wires")

Bad Example: The tops of the nodes are aligned creating a wiggly white exec line.
![Bad](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-bad.png "Wiggly")

Acceptable Example: Certain nodes might not cooperate no matter how you use the alignment tools. In this situation, try to minimize the wiggle by bringing the node in closer.
![Acceptable](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-acceptable.png "Acceptable")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 White Exec Lines Are Top Priority 

If you ever have to decide between straightening a linear white exec line or straightening data lines of some kind, always straighten the white exec line.

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Graphs Should Be Reasonably Commented 

Blocks of nodes should be wrapped in comments that describe their higher-level behavior. While every function should be well named so that each individual node is easily readable and understandable, groups of nodes contributing to a purpose should have their purpose described in a comment block. If a function does not have many blocks of nodes and its clear that the nodes are serving a direct purpose in the function's goal, then they do not need to be commented as the function name and  description should suffice.

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Graphs Should Handle Casting Errors Where Appropriate 

If a function or event assumes that a cast always succeeds, it should appropriately report a failure in logic if the cast fails. This lets others know why something that is 'supposed to work' doesn't. A function should also attempt a graceful recover after a failed cast if it's known that the reference being casted could ever fail to be casted.

This does not mean every cast node should have its failure handled. In many cases, especially events regarding things like collisions, it is expected that execution flow terminates on a failed cast quietly.

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Graphs Should Not Have Any Dangling / Loose / Dead Nodes 

All nodes in all blueprint graphs must have a purpose. You should not leave dangling blueprint nodes around that have no purpose or are not executed.

**[⬆ Back to Top](#table-of-contents)**
