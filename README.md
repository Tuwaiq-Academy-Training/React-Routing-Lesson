# React-Styling-Routing-Lesson
# تنسيق المكونات


# المقدمة

لإضافة تنسيق style للصفحة، سنقوم باستعمال CSS (Cascading Style Sheets) والتي تستعمل عادة مع HTML لإضافة التنسيقات الشكلية والتي تقوم بوصف كيفية عرض العناصر في الصفحة، كاللون والحجم والخط وغيره.


***طريقة الكتابة***

يُكتب بداية الSelector والذي يقوم بتحديد العنصر/العناصر المُراد تطبيق التنسيق عليها، ثم تحدد الخاصية وقيمتها المُراد تطبيقها على العنصر المُختار.

![](https://paper-attachments.dropbox.com/s_B6106E77D59D24577BBEA3D05FBC34D344DE96D16C04EE13C1D73E84F9F6CBAF_1626730593755_Screenshot+2021-07-20+003620.png)


 
***اختيار العنصر باستعمال Selector ينقسم إلى عدة أنواع، منها:***


- * والتي تعني جميع العناصر الموجودة في الصفحة.
- باستعمال اسم العنصر مثل h1
- باستعمال اسم الclass كالتالي example. 
- باستعمال اسم الid كالتالي example# 
- يمكنك التحديد باستعمال أكثر من نوع مثل h1.example
- يمكنك تجميع أكثر من نوع مثل h1, h2, h3


***أنواع إضافة تنسيق مع React*** 

***يمكن إضافة CSS لReact بعدة طرق منها:***

- تنسيق Inline
    يُكتب هذا النوع داخل tag البداية للعنصر ويكون باستعمال خاصية style وإضافة التنسيق داخل {{ }}، ويُنبه على أن كتابة css هنا يكون بأسلوب camelCase. في حال أردنا تطبيق تنسيق inline للمكوّن السابق الذي أنشأناه:


    import React, { Component } from 'react';
        export default class Example extends Component {
          render() {
            return <h1   
                    style={{ 
                    backgroundColor: 'gray', 
                    fontSize: '20px' 
                  }}> Hello tuwaiq students </h1>;
          }
        }


- انشاء ملف تنسيق منفصل بامتداد css 

لاستعمال هذا النوع علينا أولًا تحديد اسماء الclasses و الids لكل عنصر، أو تركه بدون تحديد في حال رغبنا باستعمال اسم العنصر لاختياره.


    import React, { Component } from 'react';
    import './Example.css';
    export default class example extends Component {
      render() {
        return (
          <div className="container">
            <h1> Hello tuwaiq students </h1>;
            <h2 id="text"> Did you like css? </h2>
          </div>
    )
      }
    }

ثم نقوم بانشاء ملف منفصل بامتداد css وليكن Example.css، ثم نقوم بتحديد التنسيق لكل عنصر مُراد، ونتأكد من استدعاء الملف في بداية صفحة المكوّن المُراد تطبيق التنسيق عليه.


      h1 {
          font-size: 20px;
          color: #fff;
      }
    
      .container {
          background-color: red;
          text-align: center;
      }
    
      #text {
          color: #56D5FA;
          text-decoration: none;
      }

استخدام Function و Event Handler في React
يُمكننا React من استعمال مزايا لغة JavaScript، بما فيها كتابة المتغيرات والثوابت والدوال. تُعتبر الدالة جزءً برمجيًا معني بتنفيذ مهمة أو مهام معينة، وعادة ما يرتبط تفعيل هذه الدالة بحدث محدد (كالنقر والتغيير وتمرير الفأرة).

عندما يتم النقر في هذا المثال على زر Click me، ستفعل دالة print والمرتبطة بحدث النقر على الزر باستعمال خاصية onClick. فستظهر كنتيجة نافذة alert والتي تحتوي على كلمة Welcome.
لاحظ طريقة استدعاء الدالة هذه في مكوّن class مشروطة باستعمال this والتي تشير إلى component object.


    class Example extends React.Component {
      print() {
        alert("Welcome");
      }
      render() {
        return (
          <button onClick={this.print}>Click me</button>
        );
      }
    }

في حال أردنا عمل نفس المثال السابق على مكوّن functional


    import React from 'react'
    export default function Example() {
      function print() {
        alert("Welcome");
      }
      return <button onClick={print}>Click me</button>;
    }


***أنواع أخرى من الأحداث التي من الممكن التحكم بها:***

Keyboard events:

- onKeyDown يعمل عندما يكون أحد مفاتيح لوحة المفاتيح مضغوطًا
- onKeyPress يعمل بعد إفلات المفتاح المضغوط
- onKeyUp يعمل بعد انتهاء الاثنين السابقين

Mouse events:

- onClick يعمل عندنا يتم ضغط وإفلات زر الفأرة
- onMouseDown يعمل عندنا يتم ضغط زر الفأرة لكن بدون إفلات
- onMouseUp يعمل عندنا يتم إفلات زر الفأرة
- onContextMenu يعمل عندنا يتم ضغط وإفلات زر الفأرة الأيمن
- onDoubleClick يعمل عند الضغط المزدوج
- onMouseMove يعمل عندما تتحرك الفأرة
- onMouseEnter يعمل عندنا تتحرك الفأرة فوق عنصر معين
- onMouseOut يعمل عندنا تبتعد الفأرة عن عنصر معين

Drag and drop events:

- onDrag يعمل عند سحب العنصر
- onDragStart يعمل عند بدء سحب العنصر
- onDragEnd يعمل عند انتهاء سحب العنصر
- onDrop يعمل عند افلات العنصر

Forms events:

- onChange يعمل عندما يغير المستخدم قيمة في عنصر ما
- onSubmit خاصية مخصصة للاستعمال داخل النماذج تعمل بعد ان يتم ضغط زر التسليم 

Focus events:

- onFocus يعمل عندما يتلقى عنصر تحكم التركيز
- onBlur يعمل عندما يفقد عنصر تحكم التركيز


# انشاء مكوّن باستخدام طريقة Function

***طريقة انشاء المكوّن***

داخل مجلد src نقوم بإنشاء مجلد components لإدارة وتنظيم الملفات بالطريقة المُتعارف عليها، ثم نقوم بإنشاء ملف المكوّن الجديد بامتداد js، ثم نقوم بتفعيل اختصار rfc للإضافة الهيكل الأساسي للمكوّن.

src/components/Example.js


    import React from 'react'
    function Example() {
     return <h1> Hello tuwaiq students </h1>;
    }
    
    export default Example;
    

بإمكاننا أيضًا للاختصار عمل export في بداية الملف بدلًا من نهايته.


    import React from 'react'
    export default function Example() {
     return <h1> Hello tuwaiq students </h1>;
    }


***استدعاء المكوّن***

لاستدعاء المكوّن علينا أن نذهب إلى App.js ونستدعي المكوّن في بداية الملف من components/Example ثم نقوم بإضافة الtag داخل دالة return، وسنرى نتيجة  Hello tuwaiq students مطبوعة على الشاشة.
src/App.js


    import logo from './logo.svg';
    import './App.css';
    import Example from './components/example';
    
    function App() {
      return (
        <div className="App">
          <header className="App-header">
            <img src={logo} className="App-logo" alt="logo" />
            <p>
              Edit <code>src/App.js</code> and save to reload.
            </p>
            <a
              className="App-link"
              href="https://reactjs.org"
              target="_blank"
              rel="noopener noreferrer"
            >
              Learn React
            </a>
          </header>
        <Example/>
        </div>
      );
    }
    export default App;
# انشاء مكوّن باستخدام طريقة Class

***طريقة انشاء المكوّن***

داخل مجلد src نقوم بإنشاء مجلد components لإدارة وتنظيم الملفات بالطريقة المُتعارف عليها، ثم نقوم بإنشاء ملف المكوّن الجديد بامتداد js، ثم نقوم بتفعيل اختصار rcc للإضافة الهيكل الأساسي للمكوّن.

src/components/Example.js


    import React, { Component } from 'react';
    
    class Example extends Component {
      render() {
        return <h1> Hello tuwaiq students </h1>;
      }
    }
    
    export default Example;

بإمكاننا أيضًا للاختصار عمل export في بداية الملف بدلًا من نهايته.


    import React, { Component } from 'react';
        export default class Example extends Component {
          render() {
            return <h1> Hello tuwaiq students </h1>;
          }
        }


***استدعاء المكوّن***

لاستدعاء المكوّن علينا أن نذهب إلى App.js ونستدعي المكوّن في بداية الملف من components/Example ثم نقوم بإضافة الtag داخل دالة render، وسنرى نتيجة  Hello tuwaiq students مطبوعة على الشاشة.
src/App.js


     import React, { Component } from 'react';
        import logo from './logo.svg';
        import './App.css';
        import Example from './components/Example';
    
        class App extends Component {
          render() {
            return (
          <div className="App">
          <header className="App-header">
            <img src={logo} className="App-logo" alt="logo" />
            <p>
              Edit <code>src/App.js</code> and save to reload.
            </p>
            <a
              className="App-link"
              href="https://reactjs.org"
              target="_blank"
              rel="noopener noreferrer"
            >
              Learn React
            </a>
          </header>
        <Example/>
        </div>
            );
          }
        }
    
        export default App;# وسم Router

## **مفهوم**

يُعتبر BrowserRouter الوسم الأساسي والأب الأعلى الذي يحتوي بداخله بقية المكوّنات. يُفضل الناس عادة تسميته Router للاختصار.

## **طريقة الاستعمال**

نقوم أولًا باستدعاء BrowserRouter من مكتبة `react-router-dom` بهذا الشكل:


    import { BrowserRouter } from 'react-router-dom'
    // أو نستعمل هذه التسمية
    import { BrowserRouter as Router} from 'react-router-dom'

بإمكاننا أيضًا استعمال التسمية المُتعارف عليها Router من خلال اضافة as Router

بعد الاستدعاء نقوم بإحاطة المكوّن الأساسي App بوسم Router لأننا كما ذكرنا يُعتبر الأب الأعلى لجميع المكوّنات.


    ReactDom.render(<Router> <App /> </Router>)
## **مثال**
    import React from 'react';
    import { render } from 'react-dom';
    import { BrowserRouter as Router  } from 'react-router-dom';
    import './index.css';
    
    render(
      <Router>
        <App />
      </Router>,
      document.getElementById('root')
    );

# وسم Route

## **مفهوم**

يُستخدم وسم Route لتحديد المسار والمكوّن المرتبط به 


## **طريقة الاستعمال**

لتحديد المسار الذس سيتم إضافته للURL يتم استعمال خاصية path والتي تبدأ ب/ مع كتابة الكلمة الانتقالية. أما في خاصية component فيتم تحديد المكوّن المُراد ربطه بهذا الURL وعرضه.


    <Route path="/settings" element={<SettingsPage/>} />

قد نرغب أحيانًا بجعل المكوّن ظاهرًا في كل الصفحات، لفعل ذلك نقوم فقط بإضافة / في خاصية المسار path والتي ستكون موجودة في الURL دائمًا بغض النظر عن المكوّن الذي يتم عرضه. من أمثلة استعمال هذا المسار إدراج bar أو footer في جميع صفحات الموقع.


    <Route path="/" element={<NavBar/>} />

نلاحظ هنا أنه بمجرد ظهور الرمز / سيتم إظهار المكوّن المرتبط به. نستنتج من هذه الملاحظة أن ظهور الpath كجزء أو ككل من الURL كافٍ للانتقال إلى المكوّن. لتفادي هذا الأمر وجعل المتصفح ينتقل للمكوّن فقط في حاله تطابق المسار تمامًا من كامل الURL نستعمل كلمة exact كما هو موضح في المثال:


    <Route exact path="/" element={<HomePage/>} />

وبهذا لن ينتقل المتصفح إلى Home إلا في حال كان الURL مكوّن فقط من الرمز /


## **مثال**
    import React from 'react';
    import { render } from 'react-dom';
    import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
    import './index.css';
    
    render(
       <Router>
        <Route exact path="/" element={<HomePage/>}></Route>
        <Route path="/" element={<NavBar/>}></Route>
        <Route path="/settings" element={<SettingsPage/>} />
      </Router>
      document.getElementById('root')
    );

 Routes

***مفهوم***

يستخدم Routes لاختيار Route واحد لعرضه حتى في حال تطابق أكثر من path مع الURL. 

مثال

لنسترجع سويًا المثال السابق:


    import React from 'react';
    import { render } from 'react-dom';
    import { BrowserRouter as Router,Routes, Route } from 'react-router-dom';
    import './index.css';
    
    render(
       <Router>
        <Route exact path="/" element={<HomePage/>}></Route>
        <Route path="/" element={<NavBar/>}></Route>
        <Route path="/settings" element={<SettingsPage/>} />
      </Router>
      document.getElementById('root')
    ); 

على سبيل المثال في حال كان الURL عبارة عن / فسيعرض بطبيعة الحال HomePage و NavBar. لكن في حال وضعنا Routes فسيعرض أول تطابق فقط.


    import React from 'react';
    import { render } from 'react-dom';
    import { BrowserRouter as Router,Routes, Route } from 'react-router-dom';
    import './index.css';
    
    render(
       <Router>
        <Routes>
        <Route exact path="/" element={<HomePage/>}></Route>
        <Route path="/" element={<NavBar/>}></Route>
        <Route path="/settings" element={<SettingsPage/>} />
        <Routes>
      </Router>
      document.getElementById('root')
    );

سيقوم هنا بعرض HomePage فقط دون NavBar.

# وسم Link

## **مفهوم**

إن وسم <Link> شبيه جدًا بوسم <a>، إلا أنه مختلف من ناحية عدم تحديث الصفحة عند الانتقال بواسطته.

## **طريقة الاستعمال**

نقوم باستعمال خاصية to لتحديد الهدف المراد الانتقال إليه. ثم نكتب الكلمة أو الكلمات المراد ظهورها كرابط تنقل بين وسم البداية والنهاية بهذا الشكل:


    <Link to=“/settings”>Settings</Link>

نلاحظ أن الرابط سيتغير بعد الانتقال وسيضاف إليه /settings ولكن بدون تحديث الصفحة. نلاحظ أيضًا أن هذا المسار هو نفس المسار الذي تم تعريفه مسبقًا داخل Route.

## **مثال**
    import React, { Component } from 'react'
    export default class App extends Component {
      render() {
        return (
          <div>
            <nav>
              <Link to='/'> Home </Link>
              <Link to='/settings'> Settings </Link>
            </nav>
          </div>
        )
      }
    }


