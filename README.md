# React-Routing-Lesson

# سوف نتعلم في هذا الدرس :
 
* التنقل بين الصفحات باستخدام BrowserRouter


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

إن وسم <Link>  شبيه جدًا بوسم  <a> , إلا أنه مختلف من ناحية عدم تحديث الصفحة عند الانتقال بواسطته.

## **طريقة الاستعمال**

نقوم باستعمال خاصية to لتحديد الهدف المراد الانتقال إليه. ثم نكتب الكلمة أو الكلمات المراد ظهورها كرابط تنقل بين وسم البداية والنهاية بهذا الشكل:


    <Link to=“/settings”>Settings</Link>

نلاحظ أن الرابط سيتغير بعد الانتقال وسيضاف إليه /settings ولكن بدون تحديث الصفحة. نلاحظ أيضًا أن هذا المسار هو نفس المسار الذي تم تعريفه مسبقًا داخل Route.

 
## **مثال**
```js
 
 import React, { Component } from 'react'
 
 import {Link} from "react-router-dom";
 
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

```
