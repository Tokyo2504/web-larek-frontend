# Проектная работа "Веб-ларек"

Стек: HTML, SCSS, TS, Webpack

Структура проекта:
- src/ — исходные файлы проекта
- src/components/ — папка с JS компонентами
- src/components/base/ — папка с базовым кодом

Важные файлы:
- src/pages/index.html — HTML-файл главной страницы
- src/types/index.ts — файл с типами
- src/index.ts — точка входа приложения
- src/scss/styles.scss — корневой файл стилей
- src/utils/constants.ts — файл с константами
- src/utils/utils.ts — файл с утилитами

## Установка и запуск
Для установки и запуска проекта необходимо выполнить команды

```
npm install
npm run start
```

или

```
yarn
yarn start
```
## Сборка

```
npm run build
```

или

```
yarn build
```
## Архитектура  
Приложение реализовано с помощью MVP архитектуры.
![схема1](https://github.com/user-attachments/assets/03a5dd0a-afd1-4cc7-a163-1b4160e73145)  

## Базовые классы
 ### 1. Класс ```Model```

Абстрактный класс, предназначенный для реализации работы с данными в различных моделях.  

**Свойства:**  
```data```: хранит данные объекта.  
```events```: хранит объект для работы с событиями.  

**Методы:**  
```emitChanges```: уведомляет об изменении состояния модели.  

### 2. Класс ```Component```

Абстрактный класс, предоставляющий базовые методы для работы с DOM-элементами и управления их состоянием.  

**Свойства:**  
```container```: контейнер, в котором размещается компонент.  
```events```: объект, реализующий интерфейс для работы с событиями.  

**Методы:**   
```toggleClass```: добавляет или удаляет CSS-класс указанного элемента.  
```setText```: устанавливает текстовое содержимое элемента.  
```setDisabled```: добавляет или удаляет атрибут disabled.  
```setHidden```: скрывает элемент, устанавливая ```display = none```.  
```setVisible```: показывает элемент, изменяя его тип видимости с ```display = none```.  
```setImage```: добавляет изображение в элемент ```img``` и изменяет его атрибуты ```src``` и ```alt```.  
```render```: рендер компонента в виде DOM-элемента.  

### 3. Класс ```Api```

Класс представляет собой обертку для взаимодействия с API, предоставляет методы для выполнения HTTP-запросов и обрабатывает ответы от сервера.  

**Свойства:**  
```baseUrl```: базовый URL для работы с API.  
```options```: объект с настройками для HTTP-запроса.  

**Методы:**   
```handleResponse```: обрабатывает ответ от API, преобразует и возвращает его.    
```get```: выполняет GET-запрос по указанному URL.  
```post```: выполняет POST-запрос по указанному URL.  

### 4. Класс ```EventEmitter```

Класс позволяет подписываться на события и уведомлять подписчиков о наступлении события.  

**Свойства:**  
```events```: хранит события и их подписчиков.  

**Методы:**   
```off```: снимает обработчки с события.  
```onAll```: слушает все события.  
```offAll```: сбрасывает все обработчики.  

## Модели данных
### 1. Класс ```Product```

Класс используется для хранения и управления данными товара.  

**Свойства:**  
```id```: идентификатор товара.  
```description```: описание товара.  
```image```: изображение товара.  
```title```: название товара.  
```category```: категория товара.  
```price```: цена товара.  

**Методы:**  
```set id```: устанавливает идентификатор товара.  
```set description```: устанавливает описание товара.  
```set image```: устанавливает изображение товара.  
```set title```: устанавливает название товара.  
```set category```: устанавливает категорию товара.  
```set price```: устанавливает цену товара.  

### 2. Класс ```Order```

Класс используется для хранения и управления данными заказа. Методы позволяют валидировать данные заказа.  

**Свойства:**  
```items```: массив товаров в заказе.  
```total```: общая сумма заказа.  
```email```: электронная почта покупателя.  
```phone```: телефон покупателя.  
```payment```: способ оплаты.  
```address```: адрес доставки покупателя.  
```formErrors```: ошибки формы.  

**Методы:**  
```validateOrder```: проверка валидности всего заказа.  
```validateEmail```: проверка валидности электронной почты.  
```validatePhone```: проверка валидности телефонного номера.  
```validatePayment```: проверка валидности способа оплаты.  
```validateAddress```: проверка валидности адреса доставки.  
```resetOrder```: сброс данных заказа.  
```set items```: устанавливает товары в заказе.  
```set total```: устанавливает общую сумму заказа.  
```set email```: устанавливает электронную почту.  
```set phone```: устанавливает телефон.  
```set payment```: устанавливает способ оплаты.  
```set address```: устанавливает адрес доставки.  

### 3. Класс ```AppData```

Класс управляет состоянием приложения.     

**Свойства:**  
```catalog```: мссив товаров в каталоге.  
```basketItems```: массив товаров в корзине.  
```order```: объект текущего заказа.  
```preview```: просмотр выбранного товара.  

**Методы:**  
```createNewOrder```: создает новый объект заказа.  
```calculateTotal```: вычисляет общую сумму товаров в корзине.  
```clearBasket```: очищает корзину.  
```setCatalog```: устанавливает каталог товаров.  
```setPreview```: устанавливает предварительный просмотр товара.  
```listBasketItemIds```: возвращает список ID товаров в корзине.  
```countBasketItems```: возвращает количество товаров в корзине.  
```addToBasket```: добавляет товар в корзину.  
```removeFromBasket```: удаляет товар из корзины по ID.  

## Классы отображения
### 1. Класс ```PageView```

Класс отвечает за отображение всей страницы.  

**Свойства:**  
```catalog```: элемент, представляющий каталог товаров.  
```counter```: элемент, отображающий счетчик количества товаров в корзине.  
```wrapper```: контейнер для основного содержимого страницы.  
```basket```: элемент, представляющий корзину.  

**Методы:**  
```counter```: обновляет значение счетчика на странице.  
```catalog```: обновляет содержимое каталога.  
```locked```: управляет состоянием блокировки страницы.  

### 2. Класс ```ProductView```

Класс отвечает за отображение данных продукта.  

**Свойства:**  
```id```: элемент, представляющий идентификатор продукта.  
```description```: элемент для отображения описания продукта.  
```image```: изображения продукта.  
```title```: элемент, отображающий название продукта.  
```category```: элемент для отображения категории продукта.  
```price```: элемент для отображения цены продукта.  
```button```: кнопка продукта.  

**Методы:**  
```set id```: устанавливает идентификатор продукта в элемент.  
```set description```: устанавливает описание продукта в элемент.  
```set image```: используется для обновления изображения продукта в интерфейсе.  
```set title```: обновляет название продукта в элементе интерфейса.  
```set category```: обновляет категорию продукта в соответствующем элементе.  
```set price```: обновляет цену продукта в элементе интерфейса.  
```set button```: устанавливает текст или действие для кнопки продукта.  

### 3. Класс ```BasketView```

Класс отвечает за отображение корзины товаров.  

**Свойства:**  
```list```: элемент для отображения списка товаров в корзине.  
```total```: элемент для отображения общей суммы товаров в корзине.  
```button```: кнопка для выполнения действий в корзине.  

**Методы:**  
```set items```: устанавливает список элементов корзины для отображения.  
```set total```: устанавливает значение для отображения общей стоимости корзины.  
```setButtonState```: управление доступностью кнопки в зависимости от того, выбраны элементы или нет.  

### 4. Класс ```BasketItemView```

Класс отвечает за отображение элемента в корзине.  

**Свойства:**  
```title```: элемент, который отображает название товара.  
```index```: элемент, который отображает индекс (порядковый номер) товара в корзине.  
```price```: элемент, который отображает цену товара.  
```removeButton```: кнопка удаления товара из корзины.

**Методы:**  
```set title```: устанавливает название товара.  
```set price```: устанавливает цену товара.  
```setItemPosition```: устанавливает позицию товара в корзине.  

### 5. Класс ```FormView```

Класс представляет собой отображение формы.  

**Свойства:**  
```submit```: кнопка отправки формы.  
```errors```: элемент для отображения ошибок в форме.  

**Методы:**  
```set valid```: управляет состоянием кнопки отправки формы.  
```set errors```: обновляет элемент, который отображает ошибки формы.  
```render```: рендерит форму.  
```onInputChange```: обрабатывает изменение значений в поле формы.  

### 6. Класс ```ContactsFormView```  

Класс отвечает за отображение формы контактной информации.   

**Методы:**  
```set email```: устанавливает значение для поля email в форме.  
```set phone```: устанавливает значение для поля телефона в форме.  

### 7. Класс ```DeliveryFormView```

Класс отвечает за отображение и управление формой для ввода данных о способе платежа и адресе.  

**Свойства:**  
```buttons```: кнопки для выбора типа оплаты.  
```container```: контейнер кнопок оплаты. 

**Методы:**  
```set payment```: устанавливает выбранный метод оплаты в форму.  
```set address```: устанавливает адрес доставки в форму.  
```setActivePaymentButton```: делает активной кнопку, соответствующую выбранному методу оплаты.  
```handlePaymentClick```: обрабатывает клики на кнопки выбора метода оплаты.  

### 8. Класс ```ModalView```

Класс предназначен для управления модальными окнами.  

**Свойства:**  
```content```: элемент, представляющий содержимое модального окна.  
```button```: кнопка управления модальным окном. 

**Методы:**  
```open```: открывает модальное окно.  
```close```: закрывает модальное окно.  
```setContent```: устанавливает содержимое модального окна.  
```render```: рендерит модальное окно на странице.  

### 9. Класс ```SuccessView```

Класс отображает успешное завершение оформления заказа.    

**Свойства:**  
```total```: элемент, который отображает общую сумму покупки.  
```closeButton```: кнопка для подтверждения оформления заказа и закрытия окна.  

**Методы:**  
```set total```: устанавливает значение для отображения общей суммы заказа. 

## Презентер
### 1. Класс ```Presenter```
Отвечает за взаимодействие между моделями данных и отображением.  

**Свойства:**  
```events```: объект для работы с событиями.  
```api```: используется для получения данных, которые затем передаются в отображение.  

**Методы:**   
```loadProducts```: загружает список продуктов.  
```loadProductById```: загружает информацию о конкретном продукте по ID.  
```submitOrder```: отправляет данные о заказе.

## Служебные классы
### 1. Класс ```ProductApi```
Класс для взаимодействия с API, обеспечивающий методы для получения информации о продуктах и отправки данных о заказах.  

**Свойства:**  
```cdn```: URL для доступа к данным.  

**Методы:**   
```getProductItem```: получает информацию о конкретном продукте по ID.  
```getProductItems```: получает список всех продуктов.  
```sendOrder```: отправляет данные о заказе на сервер.  
 
