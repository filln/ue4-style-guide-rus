
<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Статичные меши (Static Meshes) 

### Разделы

> 4.1 [UVs](#s-uvs)

> 4.2 [LODs](#s-lods)

> 4.3 [Modular Socketless Snapping](#s-modular-snapping)

> 4.4 [Должна быть коллизия](#s-collision)

> 4.5 [Корректное масштабирование (Scale)](#s-scaled)

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 Все меши должны иметь UVs

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 Все меши должны иметь непересекающиеся UVs для карт освещения (Lightmaps) 

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs должны быть установлены корректно

Это субъективное правило относительно разных проектов, но меши, которые можно увидеть в игре на разных расстояниях, должны иметь правильные лоды.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Модульные объекты без сокетов должны аккуратно устанавливаться на карту в зависимости от размера сетки.

Это субъективное правило для разных проектов, но любые ассеты без сокетов должны соединяться вместе правильно, учитывая масштаб сетки.
Это правило не зависит от того, установлен ли размер сетки на2 или на 10. Однако если делаете ассеты для маркетплейса, то ну жно знать, что требования Епиков тут такие: привязка должна корректно работать про размере сетки 10 и больше.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 All Меши должны иметь коллизии

Независимо от того, будет ли использоваться коллизия, столкновения для мешей, все меши должны иметь правильно установленную коллизию. Это поможет движку с такими вещами как расчет столкновений, occlusion и расчет освещения. Коллизия должна быть хорошей офрмы относительно объекта.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 Все меши болжны быть масштабированы корректно

Это субъективное правило для разных проектов, масштабирование мешей должно быть корректным. Левел-дизайнеры или блюпринт-разработчики не должны настраивать масштабирование мешей, чтобы использовать их в редакторе. Масштабирование мешей в движке должно рассматриваться как переопределение масштабирования во вьюпорте, а не изменение масштабирования самого меша.

**[⬆ Back to Top](#s)**
