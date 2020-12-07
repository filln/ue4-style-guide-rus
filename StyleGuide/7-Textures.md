
<a name="7"></a>
<a name="textures"></a>
## 7. Текстуры

### Sections

> 7.1 [Размер должен быть степенью 2](#textures-dimension)

> 7.2 [Texture Density Should Be Uniform](#textures-dimension)

> 7.3 [Максимальный размер текстуры должен быть равен 8192](#textures-max-size)

> 7.4 [Correct Texture Groups](#textures-textures-group)

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Размер должен быть степенью 2

Все текстуры, исключая UI текстуры, должны иметь размер равный числу 2, возведенному в какую-либо целую степень (2^0...2^13 == 1...8192). Текстуры не обязательно должны быть квадратом.
К примеру, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 Плотность текстур должна быть постоянной для проекта.

Все текстуры должны иметь размер, соответствующий их применению. Соответствующая плотность текстур варьируется от проекта к проекту, но все текстуры в рамках этого проекта должны иметь постоянную плотность.
К примеру, если текстура проекта имеет плотность 8 пикселей на 1 юнит и должна быть на кубе размером 100х100 юнитов, то ее размер должен быть 1024х1024, так как это ближайшая степень 2, которая соответствует плотности текстур проекта. То есть 8*100 == 800. 2^9 == 512, 2^10 == 1024. 800 ближе к 1024, значит нужно брать размер текстуры 1024х1024.

[Статья про плотность текстур](https://habr.com/ru/post/315146/)

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 Максимальный размер текстуры должен быть равен 8192

Не должно быть текстур размером выше 8192, тлько если у вас нет веской причины на это. Часто использомание текстур такого размера - пустая трата ресурсов.

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 Текстуры должны быть корректно сгруппированы

Every texture has a Texture Group property used for LODing, and this should be set correctly based on its use. For example, all UI textures should belong in the UI texture group.
Каждая текстура имеет свойство Texture Group, испольуемое для LOD, поэтому группа должна быть корректно установлена. К примеру, все UI текстуры должны принадлежать группе UI.

**[⬆ Back to Top](#textures)**