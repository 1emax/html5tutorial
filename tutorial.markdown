# HTML5: Больше, чем модная фишка

# ЗАДАЧИ

Цель этого практикума - показать, как новые возможности HTML5 могут быть использованы в современных веб-приложениях без участия дополнительных зависимостей и противоречий с уже существующим кодом. Курс рассчитан на то, чтобы дать вам достаточно знаний для самостоятельного использования новых возможностей в своих приложениях.

# ПРЕДВАРИТЕЛЬНЫЕ ТРЕБОВАНИЯ

- Все упражнения проверялись в последних версиях браузера Chrome, но они должны работать и в последних версиях Safari и Firefox. Некоторые упражнения работают в Firefox не так, как задумано, из-за ограничений браузера.
Я не проверял работоспособность в IE или Opera, но большая часть кода должна работать и там.

- Ваш браузер должен иметь консоль JavaScript. Такая консоль уже имеется в Safari и Chrome. Если вы используете Firefox, не забудьте установить [Firebug](http://getfirebug.com).

- Вам понадобится текстовый редактор (Vi, Emacs, Textmate, Notepad, etc.) для внесения изменений в файлы проекта.

# УСТАНОВКА

1. Скопируйте папку `start` из этого проекта в какое-нибудь другое место. Эта папка содержит все необходимые зависимости и послужит основой для игры, которую мы будем делать.

2. Изучите файл index.html в скопированной директории `start`. Он представляет собой упрощенный шаблон, основанный на [HTML5 Boilerplate](http://html5boilerplate.com/). Здесь вы можете найти [полный шаблон](https://github.com/paulirish/html5-boilerplate/blob/master/index.html). Это отличный способ изучить особенности HTML5.

    Обратите внимание на DOCTYPE, с которого начинается этот файл. Это все, что нужно, чтобы указать браузеру, что вы используете последнюю, самую современную версию HTML.
    Кроме того, в шаблоне используются новые семантические тэги `<header>` и `<footer>`. Их можно использовать вместо менее семантической разметки вроде `<div id="header"></div>`.

3. Откройте index.html в вашем браузере. Затем откройте консоль JavaScript (в Chrome это делается через меню Вид > Разработчик > Консоль Javascript; в Safari достаточно нажать option-Apple-C). В консоли должно быть сообщение "Ваша консоль работает". Если вы не видите это сообщение, попробуйте установить Firebug или открыть файл в другом браузере. Без работающей консоли следовать этому руководству крайне затруднительно.

    Это сообщение было отправлено в консоль в файле `js/tutorial.js`. Я буду использовать этот файл для всего кода приложения.

# УПРАЖНЕНИЕ 1 
## Определение возможностей

1. Изучите файл `js/libs/modernizr`. Это библиотека [Modernizr](http://www.modernizr.com/), которая выполняет определение возможностей браузера и помогает применять стили к новым семантическим элементам HTML5. Пока рано полагаться на то, что браузеры полностью поддерживают новые возможности, поэтому крайне важно проводить определение возможностей браузера и выдавать осмысленные сообщения об ошибках в случае необходимости.

2. Чтобы подключить Modernizr, откройте текстовый редактор и добавьте в тэг `<HEAD>` файла `index.html` следующую строку:

    `<script src="js/libs/modernizr-1.7.js"></script>`

    Затем добавьте класс `no-js` к тэгу `<HTML>` во второй строке файла index.html.

3. Откройте `index.html` в браузере и посмотрите на тэг `<HTML>`. Обратите внимание на то, что класс `no-js` был заменен на ряд объявлений CSS. Эти объявления можно использовать, чтобы показывать сообщения об ошибках или для стилизации контента, предъявлемого при недоступности некоторого функционала.

4. Откройте консоль JavaScript и изучите объект Modernizr. Вы сможете выполнить все упражнения этого учебника, если все нижеприведенные свойства будут иметь значение true:

    * Modernizr.canvas
    * Modernizr.websockets
    * Modernizr.audio
    * Modernizr.geolocation
    * Modernizr.localstorage

    Если какие-либо из этих свойств не имеют значения "true", установите браузер [Chrome](http://www.google.com/chrome).

## Дополнительное задание

Используя только CSS и HTML и полагаясь на классы `touch` и `no-touch` элемента `<HEAD>`, выведите соотвествующее сообщение о том, поддерживает ли устройство пользователя тач-интерфейс. Если у вас установлен симулятор мобильной ОС (например, iOS Simulator), проверьте оба случая.

# УПРАЖНЕНИЕ 2 
## Основы рисования на canvas

1. Добавьте тэг `<canvas id="main" width="400" height="400"></canvas>` сразу после открывающего тэга `<body>` в файле `index.html`.

2. Чтобы нарисовать на canvas прямоугольник, добавьте в js/tutorial.js следующий код:
    <pre>var canvas = document.getElementById("main");
    var context = canvas.getContext("2d");
    context.fillRect(0,0,20,20);</pre>

    Рисование на canvas осуществляется в контексте canvas, а не на самом объекте canvas. В настоящее время доступен только контектс "2d". В будущем возможно появление 3D-контекста.

3. Откройте `index.html` в браузере. Вы должны увидеть черный прямоугольник.

4. Вместо `fillRect` вызовите `strokeRect` и обновите страницу в браузере. Теперь прямоугольник не закрашен.

5. Задайте свойству `fillStyle` контекста какой-нибудь цвет CSS, например, красный - "red", затем обновите страницу. Вы увидите красный прямоугольник.

    <pre>context.fillStyle = "red";</pre>

6. Чтобы отобразить текст, добавьте в `tutorial.js` следующий код и обновите страницу.

    <pre>context.font = "bold 24px sans-serif";
    context.fillStyle = "blue";
    context.fillText("HTML5",100,100);</pre>

## Дополнительное задание

Попробуйте залить прямоугольник градиентом. Для этого сначала вам нужно создать градиент (что объяснено здесь: [Dive Into HTML5](http://diveintohtml5.org/canvas.html#gradients)), а затем установить этот градиент значением свойства fillStyle.

# УПРАЖНЕНИЕ 3
## Работа с изображениями на canvas

1. Скопируйте файл `media/water.jpg` из папки `media` практикума в папку `media` вашего проекта. (Это изображение распростряняется на условиях лицензии [Creative Commons-licensed](http://www.flickr.com/photos/50183640@N05/5616041841/))

2. Выведите это изображение на canvas, добавив следующий код в `tutorial.js`:

    <pre>var img = new Image();
    img.src = "media/water.jpg";
    img.onload = function() {
      context.drawImage(img,0,110);
    };</pre>

3. Обновите страницу в браузере, чтобы увидеть картинку.

4. Добавьте два дополнительных параметра после 3 уже имеющихся, ширину и высоту области вывода для картинки:

    <pre>context.drawImage(img,0,110,200,100);</pre>

5. Обновите страницу. Размер картинки будет другим.

6. Для нашей простой игры нам понадобится файл со спрайтами `media/characters.gif`. Скопируйте его в папку `media` вашего проекта. (Я получил этот файл, лицензированный на условиях CC, от David E. Gervais, участника проекта [TomeTik](http://pousse.rapiere.free.fr/tome/))

7. Чтобы вырезать одного персонажа из файла и отобразить его на canvas, вам придется вызвать `drawImage` с 9 аргументами:

    <pre>drawImage(image,sx,sy,sw,sh,dx,dy,dw,dh);</pre>

    Назначение каждого из этих агрументов объяснено на картинке:
    ![drawImage arguments](http://images.whatwg.org/drawImage.png)

    Каждый спрайт имеет ширину и высоту в 32 пикселя. Таким образом, если вы хотите вырезать второго персонажа в верхнем ряду, да-да, этого, в красном капюшоне, вам нужно вызвать `drawImage` с такими параметрами:

    * sx = 33
    * sy = 0
    * sw = 32
    * sh = 32

    Добавьте dx, dy, dw и dh по вкусу, затем обновите страницу. Если что-то не получается, посмотрите решение в папке `ex3`.

# УПРАЖНЕНИЕ 4
## Простая анимация

1. Скопируйте `js/libs/jquery-1.5.2.js` в папку `js/libs` вашего проекта. jQuery понадобится нам для обработки событий клавиатуры и некоторых других задач.

2. Чтобы подключить jQuery, добавьте следующий тэг в конец файла index.html, перед загрузкой файла `tutorial.js`:

    `<script src="js/libs/jquery-1.5.2.js"></script>`

3. Закомментируйте большую часть кода, отвечающего за рисование. В этом упражнении мы начнем с чистого листа. Оставшийся в `tutorial.js` код должен выглядеть примерно так:

    <pre>var canvas = document.getElementById("main");
    var context = canvas.getContext("2d");

    var characters = new Image();
    characters.src = "media/characters.gif";</pre>

4. Задайте значения переменных `x` и `y` равными нулю. В этих переменных будет храниться текущая позиция игрока.

5. Задайте переменные для хранения ширины и высоты canvas. В дальнейшем мы будем менять размеры canvas динамически, поэтому имеет смысл не задавать эти переменные константами.

     <pre>var height = $(canvas).height();</pre>
     <pre>var width = $(canvas).width();</pre>

5. Задайте обработчик для обработки события `onload` объекта `characters`. После загрузки изображения персонажа клавиатурные события будут обрабатываться функцией, которую мы напишем на следующем шаге:

    <pre>$(window).keyup(move);</pre>

6. Напишите функцию `move`, которая изменяет позицию персонажа на экране в зависимости от нажатой кнопки. На предыдущем шаге мы задали обрабочик клавиатурных событий. Этот обработчик должен принимать объект `event`, передаваемый jQuery. Этот объект имеет свойство `which`, указывающий на то, какая клавиша была нажата.

    Коды клавиш:

    * Вверх = 38
    * Вниз = 40
    * Влево = 37
    * Вправо = 39

    Увеличивайте значение `x` или `y` на 10, в зависимости от того, какая клавиша была нажата. Проверяйте значения `x` и `y` на предмет выхода за границы canvas (значения не должны быть меньше нуля или больше размеров canvas).

    Если вы запутались, посмотрите как реализована эта функция в файле `ex4/js/tutorial.js`.

7. В конце тела функции `move` вызовите `context.drawImage`, чтобы вырезать изображение из файла со спрайтами и отобразить его на canvas в координатах, заданных `x` и `y`.

    Если вы запутались, посмотрите, как это сделано в файле `ex4/js/tutorial.js`.

8. Обновите страницу и опробуйте анимацию. Персонаж должен неторопливо перемещаться по экрану при нажатии на клавиши со стрелками.

9. Персонаж оставляет за собой некрасивый след. Исправить это можно путем очистки экрана перед каждым выводом персонажа. Добавьте следующий код перед вызовом `drawImage`:

    <pre>context.clearRect(0,0,width,height);</pre>

10. Если хотите, заставьте персонажа перемещаться на большее расстояние при каждом нажатии клавиши.

## Дополнительное задание

Попробуйте создать цикл анимации, который осуществлял бы вывод на экран несколько раз в секунду. Это поможет отделить обработку событий клавиатуры от отображения. Для запуска цикла вам понадобится что-то вроде:

`setInterval(runLoopFunction,interval);`

Где `runLoopFunction` - имя вашей функции, а `interval` - количество миллисекунд, которые браузер должен выдерживать между вызовами функции.

# УПРАЖНЕНИЕ 5
## Работает с формами

1. Если мы сделаем нашу игру многопользовательской, нам нужно будет знать, как зовут игроков. Давайте добавим поле, которое принимает имя пользователя и использует новые возможности HTML5. Добавьте в файл `index.html` следующую строку:

    `<input id="username" placeholder="Ваше имя">`
   
2. Обновите страницу. Если вы не видите текста "Ваше имя" в поле, проверьте значение `Modernizr.input.placeholder` в консоли JavaScript.

3. Добавьте к полю ввода аттрибут `autofocus` и обновите страницу. Если браузер поддерживает такую возможность, поле автоматически получит фокус. 

4. Опробуем в деле новый элемент формы, ползунок, с помощью которого мы можем изменять размеры персонажа. Добавьте в `index.html` следующий код (1):

    `<input id="size" type="range" min="4" max="320" step="8" value="32">`

5. Добавьте обработчик событий ползунка в файл `tutorial.js`. Обработчик должен изменять размер изображения, выводимого вызовом `drawImage`. Задать обработчик можно так:

    `$('#size').change(function() { ... });`

    Получить значение ползунка можно с помощью `$('#size').val()`

(1) Firefox не отображает этот элемент. Выполните задание в Safari или Chrome.

## Дополнительное задание

Попробуйте использовать другие элементы формы, описанные в книге [Dive Into HTML5](http://diveintohtml5.org/forms.html). В HTMl5 есть даже элемент для выбора цвета!

# УПРАЖНЕНИЕ 6
## Локальное хранилище

**Примечание**: Это упражнение работает некорректно в Firefox из-за бага в обработке ссылок file://. Если вы хотите, чтобы все заработало и в Firefox, придется отдавать веб-страницу с сервера. [Подробности](https://bugzilla.mozilla.org/show_bug.cgi?id=507361)

1. Сохраните значение в локальном хранилище из консоли JavaScript:

    <pre>localStorage.setItem('shaz','bot')</pre>

2. Закройте страницу, затем откройте ее в новом окне и введите в консоли JavaScript такую команду:

    <pre>localStorage.getItem('shaz')</pre>

    Если ваш браузер поддерживает локальные хранилища, функция должна вернуть значение `shaz`.

3. Попробуйте проделать то же самое с объектом `sessionStorage`. Чем `sessionStorage` отличается от `localStorage`? Что происходит, если вы просто обновляете страницу? Одинаково ли ведут себя объекты?

4. Вызовите `localStorage.clear()` и попробуйте еще раз найти элемент 'shaz'.

5. Добавьте обработчик события `change` для поля ввода имени пользователя, которое мы создали в упражнении 5:

    <pre>$('#username').change(function() { ... });</pre>

6. В обработчике сохраните имя пользователя с помощью `localStorage`. Чтобы вызвать событие `change` вам, возможно, нужно будет снять фокус с поля ввода.  Чтобы получить значение поля ввода, используйте `$("#username").val()`.

7. Добавьте в `tutorial.js` код для получения имени пользователя из `localStorage` (которое мы сохранили на предыдущем шаге) при загрузке страницы. Если имя пользователя найдено в хранилище, восстановите ранее сохраненное имя пользователя в поле ввода, например так: `$("#username").val(nameStr)`.

8. Обновите страницу. Введите имя пользователя, снимите фокус с поля (чтобы убедиться, что событие `change` вызвано), затем снова обновите страницу. На этот раз поле ввода должно содержать имя пользователя вместо текста по умолчанию.

9. Попробуйте сохранять и извлекать из локального хранилища числа и хэши. Сохраняет ли локальное хранилище тип?

*Консоль JavaScript может обладать функцией просмотра локального хранилища и хранилища сессии. В инструменте для разработчиков движка WebKit содержимое хранилищ можно посмотреть на соответствующей вкладке.*

## Дополнительное задание

1. Добавьте к объекту `window` обработчик события `storage`, чтобы отслеживать добавление новых элементов в локальное хранилище. Если не знаете, с чего начать, начните отсюда: [Dive Into HTML5](http://diveintohtml5.org/storage.html#storage-event).

2. Что произойдет, если попытаться обратиться к элементу, которые не был сохранен в хранилище?

# УПРАЖНЕНИЕ 7
## Очистка canvas

1. Прежде, чем добавить в нашу "игру" возможности мультиплеера, поработаем над ее внешним видом. Установим для canvas темный фон. Добавьте этот код в тэг `<head>` файла `index.html`:

        <style>
          canvas { 
            background-color: black;
          }

          input { display: block; }
        </style>

2. Если хотите, можно увеличить ширину и высоту canvas.

3. Увеличьте скорость перемещения персонажа так, чтобы он перемещался на 5 или 10 пикселей на одно нажатие клавиши.

# УПРАЖНЕНИЕ 8
## Web Sockets

**Примечание**: WebSockets не работают в Firefox. Вы можете исправить это (частично) с помощью [socket.io](http://socket.io/).

1. Подключим websocket-сервер для обмена информацией с другими игроками. Добавьте в `tutorial.js` код, приведенный ниже. Я заметил, что если этот код выполняется до загрузки `characters.gif`, это иногда приводит к ошибкам. Возможно, имеет смысл вставить этот код в обработчик события `onload` картинки. Если вам непонятно, о чем речь, загляните в решение для упражнения 8.

    <pre>var ws = new WebSocket("ws://exp.subelsky.com:8011");
    ws.onmessage = handleMessage;

    function handleMessage(event) {
      console.info(event.data);
    }</pre>

2. Обновите страницу. Каждые 10 секунд с сервера должно приходить сообщение "ping". Обратите внимание, что это сообщение - JSON-строка, поэтому прежде чем работать с ней, ее надо десериализовать.

3. Откройте `server/server.rb`, чтобы понять, к чему мы подключаемся.

4. Измените функцию `handleMessage`, добавив разбор JSON-строки. Если ваш браузер не имеет встроенной поддержки JSON, подключите к проекту скрипт `js/libs/json2.js`.

    <pre>var msg = JSON.parse(event.data);
    console.info(msg);</pre>

5. Обновите страницу, подождите 10 секунд и проверьте консоль. Вы должны увидеть десериализованный JSON-объект.

6. Измените функцию `move`, добавив в нее оправку JavaScript-объекта в websocket каждый раз при перемещении персонажа. Воспользуйтесь методом `websocket.send`:

    <pre>ws.send(JSON.stringify({ name: name, x: x, y: y, type: "move" }));</pre>

7. Посмотрите логи сервера, выводимые на экран. Каждый раз при нажатии клавиши перемещения в логе должны появляется сообщения о перемещении персонажа.

Если вы подумываете о создании приложения с использованием websocket, обязательно посмотрите проект [Pusher](http://pusherapp.com/). Возможно, вам не придется писать собственный сервер.

## Дополнительное задание

Сервер передает события передвижения всему классу *(практикум проводился на конференции, компьютеры студентов были объединены в сеть - прим. пер.)*. Чтобы отобразить перемещения других студентов на экране, нужно отследить их имена и координаты x и y (реализовать это лучше с помощью кэша, ключами которого будут имена пользователей, а значениями - координаты). Измените вывод `handleMessage` так, чтобы он давал информацию о нескольких игроках, показывая другую картинку для чужих персонажей. 

Мы не проверяем имена пользователей на уникальность, поэтому постарайтесь сразу договориться с другими студентами о разных именах.

# УПРАЖНЕНИЕ 9
## Работа с мультимедия (и пользовательскими аттрибутами)

Добавим в игру звуковые эффекты и воспользуемся пользовательскими аттрибутами HTML5 для упрощения управления.

1. Добавьте в тело `index.html` такой список:

        <ul>
          <li><a href="#" data-soundname='bubble'>Бульк</a></li>
          <li><a href="#" data-soundname='ray_gun'>Пыщь</a></li>
        </ul>

2. С помощью jQuery добавьте обработчик события `click` для тэга `<a>`. Определить, какой звук требуется проиграть, можно спомощью значения пользовательского аттрибута события, как это показано ниже. Здесь я использовал кросс-браузерное решение, а также вариант, предложенный в [спецификации HTML5](http://dev.w3.org/html5/spec/elements.html#embedding-custom-non-visible-data), который, похоже, поддерживает только Chrome.

        $('a').click(function(evt) {
          // не слишком элегантно, зато работает во всех браузерах
          $('#'+evt.target.getAttribute('data-soundname'))[0].play();

          // спецификация HTML5 предлагает изящный API, но работает это, по-видимому, только в Chrome
          // $('#'+evt.target.dataset.soundname)[0].play();
        });

    Не стоит путать пользовательские аттрибуты с микро-данными - они не предназначены для внешней обработки.  Подробне о микроданных можно почитать в [Dive Into HTML5](http://diveintohtml5.org/extensibility.html).

3. Обновите страницу. Щелкните каждую ссылку, чтобы убедиться, что свойство `dataset` доступно и получает нужное значение.

4. Воспроизведение звука и видео в HTML5 подразумевает возню с кодеками. Обычно контект доступен в нескольких форматах. Я добавил звуковые файлы в четырех разных форматах. Скопируйте звуковые файлы из папки `media` в ваш проект. Если вы отдаете эти файлы с сервера (а не через file://), возможно, вам придется повозиться в MIME, так как HTML5 не будет воспроизводить файлы, отданные с неверным MIME типом. Подробнее см. [MIME Types](http://diveintohtml5.org/video.html#video-mime-types).

    Следующий код должен работать для большинства пользователей. Спецификация предприсывает браузеру воспроизводить первый источник, который он способен воспроизвести.

        <div style="display:hidden">
          <audio id="bubble" preload>
            <source src="media/bubble.ogg">
            <source src="media/bubble.mp3">
            <source src="media/bubble.wav">
          </audio>

          <audio id="ray_gun" preload>
            <source src="media/ray_gun.ogg">
            <source src="media/ray_gun.mp3">
            <source src="media/ray_gun.wav">
          </audio>
        </div>

    Я решил добавить звуковые файлы прямо в страницу. В этом случае, если HTML5-аудио не сработает, браузер обработает их как обычно. А вообще аудио-объекты можно создавать также, как и картинки:

        var audio = new Audio;
        audio.src = "http://...";

5. Обновите страницу. Попробуйте проиграть оба файла в консоли:

    <pre>$('#bubble')[0].play()
    $('#ray_gun')[0].play()</pre>

6. Измените ссылку так, чтобы указанные файлы воспроизводились автоматически. Воспользуйтесь кодом из предыдущего шага.

7. Чтобы посмотреть, как выглядят элементы управления звуком по умолчанию, уберите стиль `display:hidden` для `<div>` и добавьте аттрибут `controls` после `preload`. Обновите страницу.

8. Вставка видео происходит также. Для обеспечения совместимости придется предоставить несколько форматов видео.  Скопируйте файлы `short.mov`, `short.mp4`, `short.ogv` и `short.webm` из папки `media` в папку `media` вашего проекта.

    Видео было сконвертировано из файла QuickTime с помощью `ffmpeg2theora`, `ffmpeg` и `HandBrakeCLI`. Настройки конвертации были подсмотрены в [Dive Into HTML5](http://diveintohtml5.org/video.html).

9. Добавьте в конец `index.html`:

          <video width="320" height="240" preload controls>
            <source src="media/short.ogg" type='video/ogg; codecs="theora, vorbis"' />
            <source src="media/short.mp4" />
            <source src="media/short.mov" />
          </video>

10. Обновите страницу. Один из видеофайлов должен отобразиться в вашем браузере.

    Потрясающий пример использования canvas для манипулирования изображением из видео можно найти [здесь](http://html5demos.com/video-canvas). В этом [this demo](http://html5demos.com/video) показано использование событий вставленного медиаконтента для отображения таймера.

## Дополнительное задание

Если воспроизведение мультимедия на поддерживается браузером, воспользуйтесь флеш-плеером [FlowPlayer](http://flowplayer.org/) (для этого нужно добавить тэг `<object>` после тэгов `<source>`. Подробно эта техника освещена в статье [Video for Everybody](http://camendesign.com/code/video_for_everybody).

# EXERCISE TEN
## Geolocation

1. At the JavaScript console, type the following command:

    <pre>navigator.geolocation.getCurrentPosition(function(loc) { console.info(loc.coords) }, function(err) { console.error(err) })</pre>

2. Inspect the location object in the console. If you lookup those coordinates in Google Maps you should get a result fairly close to the convention center! It's very easy to integrate this info
with Google Maps to show a map at the user's location, but unfortunately this can't be done from localhost due to Google Maps API authentication issues. 
[This link](http://html5demos.com/geo) has a simple demo - be sure to view source on the page.

    The first callback gets fired if the browser can guess its location. The second callback fires if it can't. For me, the second callback fired in
    Safari when I ran it on a machine with an Ethernet connection.

## Extra Credit

Check out [SimpleGeo](https://simplegeo.com/docs/tutorials/javascript) for some examples of other cool things you can do when you know a user's approximate location.

# EXERCISE ELEVEN
## Web Workers

1. Examine the file `js/worker.js` and then copy it to your project. This is a simple brute-force algorithm to find all the factors of a given integer.

2. Reload the page, then type these lines at your JavaScript console:

    <pre>var worker = new Worker('js/worker.js');

    worker.addEventListener('message', function(e) {
      console.info(e.data);
    },false);

    worker.postMessage(100);</pre>

    **If you are using Chrome**, you will get a security exception if you are loading index.html as a file:// URI. You can reopen Chrome with a command-line flag to circumvent the exception, though.
    This is what worked for me on OS X:

    <pre>open -n -a 'Google Chrome.app' --args --allow-file-access-from-files</pre>

    Or just use a different browser.

3. You should see the worker immediately post a response to the console. Try increasing the size of the number you pass to worker.postMessage until you get something that takes awhile to run (like 1,000,000). Notice
that your web page continues to be responsive even as this task runs in the background.

Here's a [more complicated webworker example](http://nerget.com/rayjs-mt/rayjs.html).

# EXERCISE TWELVE
## Offline Apps

1. Examine the `index.html` file in the `manifest` directory. This is a stripped-down version of the exercise 11 solution. Check out the `<html>` tag which now includes a reference to `demo.manifest.`

2. Examine `demo.manifest`.

3. If you have a packet sniffer, start it sniffing on port 80. Otherwise, make sure your JavaScript console is recording network traffic.

4. Now visit <http://files.subelsky.com/manifestdemo/index.html>

5. In your packet sniffer or JavaScript console, note that all files are being downloaded, and note the MIME type of the `demo.manifest` file (`text/cache-manifest`).

6. Now reload the page. If all goes well, the only traffic you'll see moving along the wire is a request to check the demo.manifest file, which doesn't even get downloaded since it is unchanged 
(because of the `304` HTTP response status code).

    This is the same technique you can use to make an HTML5 app "installable" on a smart phone.

## Extra Credit

Get `manifest/index.html` running on your dev machine. All you need to do is serve up the directory from the webserver (vs. from `file://`), and make sure the manifest file has the right MIME type. In Apache,
I added this directive to `httpd.conf`:

    AddType text/cache-manifest .manifest

# THAT WAS TOO EASY?

Here are some other "HTML5-ish" features that you should be aware of that didn't fit into this tutorial or are too bleeding-edge to be used reliably:

* [Microdata](http://diveintohtml5.org/extensibility.html)

* [WebGL](http://www.queness.com/post/7459/8-stunning-javascript-webgl-demonstrations)

* [HTML5 History API](http://html5demos.com/history/)

* [Alternatives to websockets](http://html5doctor.com/methods-of-communication/)

* [Polyfills to get HTML5 features working across browsers](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills) and also [Uber](http://html5doctor.com/how-to-get-all-the-browsers-playing-ball/)

* [Various CSS3 capabilities like rounded corners, 2D transforms, etc.](http://www.css3.com/)

# USEFUL URLs

* [Dive Into HTML5](http://diveintohtml5.org/)

* [HTML5 Doctor](http://html5doctor.com/)

* [HTML5 Demos](http://html5demos.com/)

* [HTML5 Rocks](http://www.html5rocks.com/)

* [Mozilla Canvas Tutorials](https://developer.mozilla.org/en/Canvas_tutorial)

* [WHATWG Living Standard](http://www.whatwg.org/specs/web-apps/current-work/multipage/)

# ACKNOWLEDGEMENTS

Thanks to [Jeff Casimir](http://jumpstartlab.com/) for helping me organize this material, and to [Mark Pilgrim](http://diveintomark.org/) for writing Dive Into HTML5 which was a big help. Any mistakes are my own of course!

# KEEP IN TOUCH

Thanks for coming to my tutorial.  I'm <mike@subelsky.com> or [@subelsky](http://twitter.com/subelsky)
on Twitter.  I love talking about HTML5, so email me if you have
questions or want to discuss interesting challenges.

Most of the techniques I discuss in this tutorial I learned building
an HTML5-powered game for programmers named EXP.  We're accepting beta
testers now, visit [exp.subelsky.com](http://exp.subelsky.com/) to signup!
