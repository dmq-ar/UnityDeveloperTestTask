# Unity Developer Test Task

Необходимо повторить результат по двум ниже описанным задачам. 

Версия Unity: 2021.1.28f1

**Часть 1. AR/3D**

Используемая технология - Vuforia. Ключ разработчика уже внесен.
Используемая сцена - Scenes/1-3D.
В папке FBX лежит трехмерная сцена со встроенной анимацией. В папке Textures можно найти необходимые для нее карты текстур. Встроенный анимационный клип должен быть разбит на 4 этапа:
1. 0-197 кадр: персонаж выпрыгивает из-за укрытия и поет песню
2. 697-726 кадр: персонаж переходит в состояние покоя
3. 726-790 кадр: персонаж стоит
4. 197-400 кадр: персонаж пританцовывает и упрыгивает в появившуюся дверь. 

1 и 4 этапы сопровождаются озвучкой, которую можно найти в папке Sound. 
Персонаж при первом появлении и во время упрыгивания за дверь плавно появляется из прозрачности и уходит в нее соответственно (alpha 0->1, 1->0). 

На объект, из-за которого выпрыгивает персонаж, и на комнату с дверью, должен быть применен маскирующий материал DepthMask.  

Ожидаемый результат: https://youtu.be/1TsviMdTrr8

Дополнительное задание: Перенести получившуюся сцену на ARFoundation:
- Реализовать две разные сцены (отдельно AR модуль и сама анимация с персонажем), загружать аддитивно. 
- Связать данные сцены через Zenject, в том числе с исопльзованием Signals.
- AR модуль получает на вход информацию об устанавливаемом виртуальном объекте и предоставляет пользователю соответствующий интерфейс по его установке в пространстве. 
- Перенести проект на использование URP и проапгрейдить материалы проекта

**Часть 2. UI**

Используемая сцена - Scenes/2-UI.
Необходимо сверстать окно главного меню согласно проекту в Figma: https://www.figma.com/file/CxpT6o0QIbc8zFmBMxE44Y/UI-Test-Task?node-id=0%3A1

Для надписей использовать пакет TextMeshPro.
- Добавить проект ViewController для данного UI для обработки нажатия на кнопки, заполнения информацией о пройденных уровнях на карточках игр и количества очков (в верхнем правом углу)
- Обратить внимание на появляющиеся плавно из прозрачности боковые стрелки при скроллинге опций меню (реализовать анимацию)
- При начислении игроку очков реализовать анимацию соответствующего UI элемента
  - Блок с цифрами меняет скейл согласно кривой EaseOutBack
  - Начисление очков происходит постепенно на некоторую сумму (например, если сейчас у игрока 57 очков и ему полагается добавить еще 5, то пользователь видит анимацию постепенно возрастающего числа: 57, 58, 59 …. 62). Можно, например, использовать кривую EaseOutQuad.
  - Звездочка слева от блока цифр делает оборот 360 градусов пока происходит начисление очков.
