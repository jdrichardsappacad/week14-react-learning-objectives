# REACT Week 14 Learning Objectives Answers

1.  **Explain how React uses a tree data structure called the virtual DOM to model the DOM**<br/>
    The virtual DOM is a copy of the actual DOM tree. Updates in React are made to the virtual DOM. React uses a diffing algorithm to reconcile the changes and send the to the DOM to commit and paint.

2.  **Create virtual DOM nodes using JSX**<br/>
    To create a React virtual DOM node using JSX, define HTML syntax in a JavaScript file.

    ```js
    const hello = <h1>Hello World!</h1>;
    ```

    Here, the JavaScript hello variable is set to a React virtual DOM h1 element with the text "Hello World!".

    You can also nest virtual DOM nodes in each other just like how you do it in HTML with the real DOM.

    ```js
    const navBar = (
      <nav>
        <ul>
          <li>Home</li>
          <li>Profile</li>
          <li>Settings</li>
        </ul>
      </nav>
    );
    ```

3.  **Use debugging tools to determine when a component is rendering**<br/>
    We use the React DevTools extension as an extension in our Browser DevTools to debug and view when a component is rendering

4.  **Describe how JSX transforms into actual DOM nodes**<br/>
    To transfer JSX into DOM nodes, we use the ReactDOM.render method. It takes a React virtual DOM node's changes allows Babel to transpile it and sends the JS changes to commit to the DOM.

5.  **Use the `ReactDOM.render` method to have React render your virtual DOM nodes under an actual DOM node**<br/>

    ```js
    import React from 'react';
    import ReactDOM from 'react-dom';
    import App from './App';

    ReactDOM.render(
      <React.StrictMode>
        <App />
      </React.StrictMode>,
      document.getElementById('root')
    );
    ```

6.  **Attach an event listener to an actual DOM node using a virtual node**<br/>
    To add an event listener to an element, define a method to handle the event and associate that method with the element event you want to listen for:

    ```js
    function AlertButton() {
      showAlert = () => {
        window.alert('Button clicked!');
      };

      return (
        <button type='button' onClick={showAlert}>
          Click Me
        </button>
      );
    }
    export default AlertButton;
    ```

7.  **Use`create-react-app` to stand up a new React application and import needed assets**<br/>

    We create the default create-react-application by typing in our terminal

    ```js
    npx create-react-app <name of app> --use-npm
    ```

    npx gives us the latest version. `--use-npm` just means to use npm instead of yarn or some other package manager

8.  **Construct a custom 'create-react-app' template and use it to start a new application**<br/>
    We have a special App Academy template which we create by using:

    ```js
    npx create-react-app --template @appacademy/react-v17 --use-npm
    ```

9.  **Pass props into a React component**<br/>
    `props` is an object that gets passed down from the parent component to the child component. The values can be of any data structure including a function (which is an object)

    ```js
    function NavBar() {
      return (
        <nav>
          <h1>Pet App</h1>
          // props being passed in component
          <NavLinks hello='world' />
        </nav>
      );
    }
    ```

    You can also interpolate values into JSX. Set a variable to the string, "world", and replace the string of "world" in the NavLinks JSX element with the variable wrapped in curly braces:

    ```js
    function NavBar() {
      const world = 'world';
      return (
        <nav>
          <h1>Pet App</h1>
          //props passes as a variable
          <NavLinks hello={world} />
        </nav>
      );
    }
    ```

    **Accessing props**
    To access our props object in another component we pass it the props argument and React will invoke the functional component with the props object.

    ```js
    function NavLinks(props) {
      return (
        <ul>
          <li>
            <a href='/hello'>{props.hello}</a>
          </li>
          <li className='selected'>
            <a href='/pets'>Pets</a>
          </li>
          <li>
            <a href='/owners'>Owners</a>
          </li>
        </ul>
      );
    }
    ```

    You can pass down **as many props keys as you want**.

10. **Destructure props**<br/>
    You can destructure the props object in the function component's parameter.

    ```js
    function NavLinks({ hello, color }) {
      return (
        <ul>
          <li>
            <a href='/hello'>{hello}</a>
          </li>
          <li className='selected'>
            <a href='/pets'>Pets</a>
          </li>
          <li>
            <a href='/owners'>Owners</a>
          </li>
        </ul>
      );
    }
    ```

11. **Create routes using components from the react-router-dom package**<br/>
    a. Import the react-router-dom package: `npm i react-router-dom'
    b. In your index.js:

    ```js
    // ./src/index.js
    import React from 'react';
    import ReactDOM from 'react-dom';
    import { BrowserRouter } from 'react-router-dom';
    import App from './App';

    const Root = () => {
      return (
        <BrowserRouter>
          <App />
        </BrowserRouter>
      );
    };

    ReactDOM.render(
      <React.StrictMode>
        <Root />
      </React.StrictMode>,
      document.getElementById('root')
    );
    ```

    Above you import your BrowserRouter with which you can wrap your entire route hierarchy. This makes routing information from React Router available to all its descendent components.

    Then in the component of your choosing, usually top tier such as App.js, you can create your routes using the Route and Switch Components

    ```js
    import { Route, Switch } from 'react';
    import Home from './components/Home';

    <Switch>
      <Route exact path='/'>
        <Home />
      </Route>
      <Route exact path='/users'>
        <Users />
      </Route>
    </Switch>;
    ```

12. **Generate navigation links using components from the react-router-dom package**<br/>
    We create links by either using React Router's `Link` or `NavLink`. They issue an on-click navigation event to a route defined in your app's router. Either renders an anchor tag with a correctly set href attribute. The difference between `Link` and `NavLink` is that NavLink has the ability to add extra styling when the path it links to matches the current path.

    **Link:**

    ```js
    import {Link} from 'react-router-dom'
    <Link to='/'>Home</Link>
    <Link to='/users'>Users</Link>
    ```

    **Navlink:**

    ```js
    <NavLink to="/">App</NavLink>
    <NavLink activeClassName="red" to="/users">Users</NavLink>
    <NavLink activeClassName="blue" to="/hello">Hello</NavLink>
    ```

13. **Use React Router params to access path variables**<br/>
    A component's props can also hold information about a URL's parameters. The router will match route segments starting at : up to the next /, ?, or #. Such segments are wildcard values that make up your route parameters.

    **Example:**

    ```js
    <Route path='/users/:userId'>
      <Profile />
    </Route>
    ```

    **Accessing Parameters**

    We access these parameters in our component by using the useParams function from react-router-dom.

    ```js
    import { useParams } from 'react-router-dom';

    function Example() {
      const params = useParams();
      // OR
      const { userId } = useParams(); //if params in route path is /:userId
    }
    ```

14. **Use React Router history to programmatically change the browser's URL**<br/>
    _**This one is important because we spent so little time on it. It is better to use History after something has happened, for example, a button click**_<br />
    The `useHistory` hook returns a history object that has convenient methods for navigation. history lets you update the URL programmatically For example, suppose you want to push a new URL when the user clicks a button. It has two useful methods:
    a. push
    b. replace

    We can push the user to the location of our choosing by naming the route we are pushing them to:

        ```js
        import {useHistory} from 'react-router-dom'

        export default function Example() {

        // history object is returned from useHistory hook and has various methods
        const history = useHistory();

        // Pushing a new URL
        const handleClick = () => history.push('/some/url');
        }
        ```

15. **Redirect users by using the <Redirect> component**<br/>
    The <Redirect> component from React Router helps you redirect users if you do not want to give access to the current Comonent/Page/Location. The component takes only one prop: to. When it renders, it replaces the current URL with the value of its `to` prop.

    ```js
        import { Redirect, useParams } from 'react-router-dom';

        const Profile = () => {
            const params = useParams();
            const { userId } = params;

            if (Number(userId) === 0) return <Redirect to="/">;

            return <h1>Hello from User Profile {userId}!</h1>
        }
        export default Profile;
    ```

16. **Use the useState hook to manage a component's state.**<br/>
    We use the useState hook to preserve values in a Component between function calls.
    The useState hook is a function that take an argument which represent a default value.
    The function returns an array with two indexes:
    a. currentState
    b. updater function

    The default state can be of any data structure.

17. **Initialize and update state within a function component.**<br/>

    ```js
    import { useState } from 'react';

    export default function Example() {
      const [count, setCount] = useState(0);

      return{
        <div>
            <h1>The count is {count}</h1>
            <button onClick={()=>setCount(prevCount=>prevCount+1)}>Increment</button>
        </div>
      }
    }
    ```

18. **Use the useEffect hook to trigger an operation as a result of a side effect.**<br/>
    useEffect is a function that takes two arguments, a callback function and a dependency array. The callback function is the 'effect'. The dependency array delegates when the useEffect function will be invoked based on state and/or props.

    By using the useEffect Hook, you tell React that your component needs to do something **after** render. React will remember the function you passed (referred to as "the effect"), and call it later after performing the DOM updates.

    We use useEffect to control our side-effects. Side effects include, manually touching the DOM, timers, data fetching, subscriptions, etc.

    ```js
    import { useEffect } from 'react';

    export default function Example() {
      const [count, setCount] = useState(0);

      useEffect(() => {
        document.title = `You have clicked the button ${count} times.`;
      }, [count]);

      return (
        <div>
          <h1>You have clicked the button {count} times</h1>
          <button onClick={() => setCount((prevCount) => prevCount + 1)}>
            Click
          </button>
        </div>
      );
    }
    ```

19. **Describe the three ways in which a re-render can be triggered for a React component.**<br/>

    1. Change in state
    2. Change in props
    3. When Context Changes
    4. forceUpdate() **Not Recommended**

20. **Optimize your application's performance by using useCallback.**<br/>
    We optimize performance by using `useCallback` when a function has been passed to a component where the component only needs to re-render based on its state or props value.

    Use case: You want to send both a function and a value to a child component. However, the child component ONLY wants to re-render based on the value, NOT the function.

    `useCallback` takes a functino and a dependency array (similar to `useEffect`)

    ```js
    import { useCallback } from 'react';

    export default function Example({ term }) {
      const hanldeClickItem = useCallback(
        (event) => console.log('You clicked me', event.target),
        [term]
      );

      return(
        <MyList term={term} onClick={handleClickItem}>
      )
    }
    ```

    Normally, the `onClick` prop would cause the child to re-render every time state in the parent component changed, even if the child was not listening for it. `useCallback` will prevent this behavior.

21. **Construct a form that can capture user data using common form inputs.**<br/>

```js
import { useState } from 'react';

function ContactUs() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [phone, setPhone] = useState('');
  const [comments, setComments] = useState('');

  return (
    <div>
      <h2>Contact Us</h2>
      <form>
        <div>
          <label htmlFor='name'>Name:</label>
          <input id='name' type='text' value={name} />
        </div>
        <div>
          <label htmlFor='email'>Email:</label>
          <input id='email' type='text' value={email} />
        </div>
        <div>
          <label htmlFor='phone'>Phone:</label>
          <input
            id='phone'
            type='text'
            onChange={(e) => setPhone(e.target.value)}
            value={phone}
          />
        </div>
        <div>
          <label htmlFor='comments'>Comments:</label>
          <textarea
            id='comments'
            name='comments'
            onChange={(e) => setComments(e.target.value)}
            value={comments}
          />
        </div>
        <button>Submit</button>
      </form>
    </div>
  );
}

export default ContactUs;
```

22. **Describe a controlled input.**<br/>
    **IMPORTANT**
    A React form input with `value` and `onChange` props.

23. **Handle form submission.**<br/>
    To submit a form we create a submission function. It takes an event as an argument.
    We must first prevent the default html actions from taking over by using `event.preventDefualt()` Then we can create a new data structure to hold our information, usually an object. This object can then be set to state, or passed to your database through your backend API using fetch.

    ```js
    const onSubmit = (event) => {
    // Prevent the default form behavior
    // so the page doesn't reload.
    event.preventDefault();

    // Create a new object for the contact us information.
    const contactUsInformation = {
        name,
        email,
        phone,
        comments
    };

    // we can now make an api call to our backend to POST our information
    ```

24. **Implement form validations.**<br/>
    Frontend validation **DOES NOT** replace backend validations.
    We can implement form validations using vanilla js in our component:

    ```js
    const validate = () => {
      const validationErrors = [];

      if (!name) validationErrors.push('Please provide a Name');

      if (!email) validationErrors.push('Please provide an Email');

      return validationErrors;
    };
    ```

    THEN:

    ```js
    const onSubmit = (e) => {

    // Prevent the default form behavior so the page doesn't reload.
    e.preventDefault();

    //create errors array
    const errors = validate();

    // If we have validation errors...
    if (errors.length > 0) {
    // Update the state to display the validation errors.
    setValidationErrors(errors);
    } else {
          //Create a new object for the contact us information.
        const contactUsInformation = {
          name,
          email,
          phone,
          comments
        };

    // clear validation errors
    setValidationErrors([]);
    }
    ```

25. a. **Create a React wrapper component**<br/>
    In React we can create a parent wrapper component that can render its children dynamically.
    Each React component has a props property called children. This is a reserved property that holds an array of all the children components wrapped by the parent component.

    b. **Create a React provider component that will manage the value of a Context**<br />
    We include the Provider Component inside the wrapper. It must include the exact key word value as a prop and pass its values in any chosen data structure. Values include strings, functions, objects etc.

    c. **Share and manage global information within a React application using Context**<br />
    We can share global information within a React application by using the createContext function from React to create a global object. We declare and export a variable with the context to make it available to other components. CreateContext accespts an argument which will be used as the default value. It will be overriden if context is defined inside the Provider Component.

    ```js
    import { createContext } from 'react';
    import {PupContext} from './context/PupContext'

    // create Context object to hold our Global information
    export const PupContext = createContext();

    //WRAPPER COMPONENT
    export default function PupProvider(props) {
      return (
        // PROVIDER
        <PupContext.Provider value={/* some value*/}>
            {props.children}
        </PupContext.Provider>;
      )
    }
    ```

    We use the wrapper to wrap a parent component with the global context. Any descendants of this component will also have access to global state.

    ```js
    //index.js file
    import {PupProvider} from './context/PupProvider'
    import App from './App'

    export default function Root() {
      return (
        <PupProvider>
          <App />
        </PupProvider>
      );
    }

    ReactDOM.render(<Root>, document.getElementById('root'))
    ```

26. **Retrieve values from a Context throughout your application**<br/>
    We retrieve values from a context using the useContext hook and the created Context.

    ```js
    import { useContext } from 'react';
    import { PupsContext } from './context/PupsContext';

    export default function PupsReveal() {
      const myPups = useContext(PupsContext);

      return (
        <div>
          <h1>Name: {myPups.name}</h1>
        </div>
      );
    }
    ```

27. **Describe the relationships between provider, consumer, and context**<br/>
    Context allows "global" data in a React application and stores a single value. A context's Provider is used to wrap a React application to enable all components in the application to access the context's value. A Consumer is a React component that reads a context's value.

### LINKS

1. [Learning Objectives, (no answers)](./learning-objectives-empty.md)
2. [Learning Objectives With Answers](./learning-objectives-filled.md)
3. [Imports CheatSheet](./imports-cheatsheet.md)
4. [Exports CheatSheet](./exports-cheatsheet.md)
5. [Imports, Exports One-to-One](./import-export-glance.md)
