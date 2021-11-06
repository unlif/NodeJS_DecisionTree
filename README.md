# NodeJS_DecisionTree
# Построение дерева решений  
В проекте использованы следующие JavaScript библиотеки для построения деревьев и леса принятий решений: Random Forest demo; Decision Tree demo.  
## Создаем обучающую выборку средствами JavaScript.  
### Обучающая выборка.
*trainingSet: data,*  
### Название атрибута, который содержит название класса, к которому относится тот или иной элемент обучающей выборки.
*categoryAttr: 'sex',*   
### Атрибут, который должен игнорироваться при построении дерева.
*ignoredAttributes: ['person']*  
### Устанавливается порог энтропии, при достижении которого останавливается построение дерева.
*entropyThrehold: 0.01*  
### Ограничение элементов обучающей выборки, при достижении которого останавливается построение дерева.
*minItemsCount: 1  
};*  
После установления всех значений, с помощью построенных классификаторов появляется возможность классифицировать другие данные, например:
*var decisionTreePrediction = decisionTree.predict(comic);*
Результатом является объект, полями которого являются названия классов, а значениями полей является количество деревьев, которые "проголосовали" за то, что классифицируемый объект принадлежит к соответствующему классу.
## Основная функциональность приложения
В приложении есть возможность сохранять атрибуты деревьев решений в базе данных и позволяет выгрузить их для редактирования.  
<br>
*router.post('/', auth, async (req, res)=>{}*  
Отправляется POST запрос на сервер по маршруту /saveresult, который сохраняет данные по схеме.  
<br>
*router.get('/:id/edit', auth, async (req, res) => {}*  
Отправляется GET запрос по маршруту /result/:id/edit, который находит нужный результат по id и отображает страницу с доступными полями для редактирования  
<br>
*router.post('/edit', auth, async (req, res) => {}*  
После внесенных всех изменений и нажатию кнопки «Сохранить результат» отправляется POST запрос на сервер по маршруту /result/edit, который сопоставляет введенные поля и сохраняет  результат с новыми значениями.  
<br>
*router.post('/remove', auth, async(req, res) =>{}*
Функция удаления результата происходит следующим образом, считывается id текущего результат и удаляется этот id с БД. Далее происходит перенаправление к списку сохраненных результатов  

## Авторизация и аутентификация
Для сохранения и редактирования, создаваемые пользователями результатов необходимо было реализовать логику авторизации, аутентификации.    
<br>
При принятии запроса на соответствующий путь, выполняется:
* /auth/login#register – обработка запроса на регистрацию пользователя и отображения страниц регистрации. 
* /auth/login – обработка запроса на аутентификацию и отображения страницы аутентификации. − /auth/logout – обработка запроса завершение сессии аутентификации.

## Дополнительные возможности приложения
В созданном проекте используется библиотека *jspdf*, которая позволяет, получить результат в формате PDF.  
Полученный результат можно будет в дальнейшем использовать при составлении отчетности.    
*function pdf() {}*  

Также реализована функция добавления отзывов для дальнейшего развития проекта.
*	router.get('/', (req, res)=>{}) – функция обработки HTTP запроса GET по пути /add– возвращает страницу для написания текста отзыва. 
*	router.post('/', async (req, res)=>{}) – функция обработки HTTP запроса POST, позволяет сохранить по схеме reviews данные веденные пользователем в БД.

