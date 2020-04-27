# README_Creating a ReactApp

Based on: [GitHub Explorer React App](https://github.com/discombobulateme/githubExplorerApp.git)

An App to explore github repositories and store searched on your local storage, using react.js

Dashboard page view

![README_Creating%20a%20ReactApp/Screen_Shot_2020-04-27_at_16.26.52.png](README_Creating%20a%20ReactApp/Screen_Shot_2020-04-27_at_16.26.52.png)

Repositories page view

![README_Creating%20a%20ReactApp/Screen_Shot_2020-04-27_at_16.45.48.png](README_Creating%20a%20ReactApp/Screen_Shot_2020-04-27_at_16.45.48.png)

## This is a main react app structure:

![README_Creating%20a%20ReactApp/IMG_4409.jpg](README_Creating%20a%20ReactApp/IMG_4409.jpg)

To create a reactApp, on the folder we want to create it: create-react-app <project name> --template=typescript when you want to use typescript, otherwise, just leave it : `create-react-app github-explorer-react-proj --template=typescript` 

This creates a project with all Babel and Typescript dependencies and configurations.

1. Clean it!: README + src/ .css, App.test.tsx, logo.svg, serviceWorker.ts
2. Clean index.tsx: deletes imports and comments
3. Clean the App.tsx component with deleted imports and just leave it a <h1>Hello</> in the middle not to have errors
4. Clean public folder: public/ favicon.ico, logos, maniest.json > index.html clean what was deleted!

- Configuring VSC Editor

    ## Configuring VSC Editor

    Right click on the project root > Generate Editor Config > set to true: `trim_trailing_whitespace = true` > and: `insert_final_newline = true` > and add line: `end_of_line = lf` 

- Configuring ESLint

    ## Configuring ESLint

    1. Add eslint as a development environment: `yarn add eslint -D`
    2. After installing, delete eslint config inside package.json
    3. Initialize eslint: `yarn eslint --init`? To check syntax, find problems and enforce code style > JavaScript modules (import/export) > React > y (using Typescript) > on Browser > Use a popular styleguide > Airbnb > JSON > no (we will use yarn, not npm) > copy all eslint extensions needed: "eslint-plugin-react@^7.19.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint@^5.16.0 || ^6.8.0 eslint-plugin-import@^2.20.1 eslint-plugin-jsx-a11y@^6.2.3 eslint-plugin-react-hooks@^2.5.0 || ^1.7.0 @typescript-eslint/parser@latest"
    4. Install it with yarn: yarn add eslint-plugin-react@^7.19.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint@^5.16.0 || ^6.8.0 eslint-plugin-import@^2.20.1 eslint-plugin-jsx-a11y@^6.2.3 eslint-plugin-react-hooks@^2.5.0 || ^1.7.0 @typescript-eslint/parser@latest remove what not needed (in red) >  
    5. Now install it in -D dev env: `yarn add eslint-plugin-react@^7.19.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint-plugin-import@^2.20.1 eslint-plugin-jsx-a11y@^6.2.3 eslint-plugin-react-hooks@^2.5.0 @typescript-eslint/parser@latest -D`
    6. I had issues installing it, had to take all ^ out, if you also do, then try: `yarn add eslint-plugin-react@7.19.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint-plugin-import@2.20.1 eslint-plugin-jsx-a11y@6.2.3 eslint-plugin-react-hooks@2.5.0 @typescript-eslint/parser@latest -D`
    7. Create .eslintignore (files that I want my eslint to ignore)

        ```jsx
        **/*.js
        node_modules
        build
        ```

    8. Add react functionality to understand typescript files exports: `yarn add eslint-import-resolver-typescript -D`
    9. Edit .eslintrc.json file

        ```jsx
        {
            "env": {
                "browser": true,
                "es6": true
            },
            "extends": [
                "plugin:react/recommended",
                "airbnb",
                "plugin:@typescript-eslint/recommended"
            ],
            "globals": {
                "Atomics": "readonly",
                "SharedArrayBuffer": "readonly"
            },
            "parser": "@typescript-eslint/parser",
            "parserOptions": {
                "ecmaFeatures": {
                    "jsx": true
                },
                "ecmaVersion": 2018,
                "sourceType": "module"
            },
            "plugins": [
                "react",
                "react-hooks",
                "@typescript-eslint"
            ],
            "rules": {
              "react-hooks/rules-of-hooks": "error",
              "react-hooks/exhaustive-deps": "warn",
              "react/jsx-filename-extension": [1,{ "extensions": [".tsx"]}],
        			"import/prefer-default-export": "off",
        			"import/extensions": [
        	      "error",
        	      "ignorePackages",
              {
                "ts": "never",
                "tsx": "never"
              }
            ]
            },
        		"settings": {
        	    "import/resolver": {
              "typescript": {}
            }
        }
        ```

- Configuring Prettier

    ## Configuring Prettier

    1. Add prettier in dev env: `yarn add prettier eslint-config-prettier eslint-plugin-prettier -D`
    2. Add to .eslintrc.json:

        ```jsx
        "extends": [
            "plugin:react/recommended",
            "airbnb",
            "plugin:@typescript-eslint/recommended",
            "prettier/@typescript-eslint",
            "plugin:prettier/recommended"
          ],
        ...
        "plugins": [
            "react",
            "react-hooks",
            "@typescript-eslint",
            "prettier"
          ],
        ...
        "rules": {
            "prettier/prettier": "error",
        ...
        ```

    3. Add prettier config file on root: prettier.config.js

        ```jsx
        module.exports = {
          singleQuote: true,
          trailingComma: 'all',
          allowParens: 'avoid',
        };
        ```

- Creating routes

    ## Creating routes

    On our design we have more than one page, we need a library to deal with this passagem from one page to another. 

    1.  Install [react router dom](https://reacttraining.com/react-router/): `yarn add react-router-dom`
    2. And its types: `yarn add @types/react-router-dom -D`
    3. Create routes folder: src/routes/index.tsx > remember that everything in react is a component, we need always to import react
    4. Now create a pages folder: src/pages/Dashboard/index.tsx

        ```jsx
        import React from 'react';

        // FunctionComponent = FC = component written in function format
        const Dashboard: React.FunctionComponent = () => {
          return <h1>Dashboard</h1>;
        }

        export default Dashboard;
        ```

    5. And another page called Repository: src/pages/Repository/index.tsx with same code, changing Dashboard for Repository
    6. ** 

        ```jsx
        // When I have a function with an empty return, we can simplify syntax from this
        const Routes: React.FC = () => {
        	return ();
        }

        // into this
        const Routes: React.FC = () => ();
        ```

    ### How things are connected

    ![README_Creating%20a%20ReactApp/IMG_4431.jpg](README_Creating%20a%20ReactApp/IMG_4431.jpg)

    ### Codes

    1. src/routes/index.tsx:

        ```jsx
        import React from 'react';
        import { Switch, Route } from 'react-router-dom';

        import Dashboard from '../pages/Dashboard';
        import Repository from '../pages/Repository';

        const Routes: React.FC = () => (
          // without Switch react Dom validates all routes at once
          // 'exact' garantees that it wont be possible to random add paths after "/""
          <Switch>
            <Route path="/" exact component={Dashboard} />
            <Route path="/repository" component={Repository} />
          </Switch>
        );

        export default Routes;
        ```

    2. src/pages/Dashboard/index.tsx:

        ```jsx
        import React from 'react';

        const Dashboard: React.FunctionComponent = () => {
          return <h1>Dashboard</h1>;
        };

        export default Dashboard;
        ```

    3. src/pages/Repository/index.tsx:

        ```jsx
        import React from 'react';

        const Repository: React.FunctionComponent = () => {
          return <h1>Repository</h1>;
        };

        export default Repository;
        ```

    4. src/App.tsx

        ```jsx
        import React from 'react';
        import { BrowserRouter } from 'react-router-dom';

        import Routes from './routes';

        const App: React.FC = () => (
          // BrowserRouter works as a path for anything that goes afer "/"
          <BrowserRouter>
            <Routes />
          </BrowserRouter>
        );

        export default App;
        ```

    5. src/index.tsx

        ```jsx
        import React from 'react';
        import ReactDOM from 'react-dom';
        import App from './App';

        ReactDOM.render(
          <React.StrictMode>
            <App />
          </React.StrictMode>,
          document.getElementById('root'),
        );
        ```

- Styled Components

    Css is global, and affects things even when you don't want it. Styled Components allows css to be scoped and not affect the entire application

    1. Add package: `yarn add styled-components` > and its types: `yarn add @types/styled-components -D`
    2. Inside of your page folder create a file: styles.ts and add a style component with what you would like to use on your css, but using the same component logic, inside a template literals ``

        ```jsx
        import styled from 'styled-components';

        export const Title = styled.h1`
          font-size: 48px;
          color: #3a3a3a;
        `;
        ```

    3. **Add VSC extension: styled components to highlight it such as css
    4. Import it into your main page file index.tsx: src/pages/Dashboard/index.tsx `import { Title } from './styles';` > and use it as a tag around the elements you want to use:

        ```jsx
        import React from 'react';

        import { Title } from './styles';

        const Dashboard: React.FunctionComponent = () => {
          return <Title>Explore repositórios no Github</Title>;
        };

        export default Dashboard;
        ```

    5. **import Google Fonts through Embed > Link > add it into our public/index.html right underneath <title>
    6. To add images: create assets folder: src/assets > import into the style file you want to import it > add it into the item you want to import it with url(${}) note that it will not have a template literal around because it is already around the whole configuration
    7. But how to use a global style? create a styles folder: src/styles/global.ts and create your component using is such as css . Remember to use template literals around it ``

        ```jsx
        import { createGlobalStyle } from 'styled-components';

        import githubBackground from '../assets/github-background.svg';

        export default createGlobalStyle`
          * {
            margin: 0;
            padding: 0;
            outline: 0;
            box-sizing: border-box;
          }

          body {
            background: #F0F0F5 url(${githubBackground}) no-repeat 70% top;
            -webkit-font-smoothing: antialiased;
          }

          body, input, button {
            font: 16px Roboto, sans-serif;
          }

          #root {
            max-width: 960px;
            margin: 0 auto;
            padding: 40px 20px;
          }

          button {
            cursor: pointer;
          }
        `;
        ```

    8.  Import it into App.ts (our main component) and involved it within fragment <></>

        ```jsx
        import React from 'react';
        import { BrowserRouter } from 'react-router-dom';

        import GlobalStyle from './styles/global';
        import Routes from './routes';

        const App: React.FC = () => (
          // BrowserRouter works as a path for anything that goes afer "/"
          <>
            <BrowserRouter>
              <Routes />
            </BrowserRouter>
            <GlobalStyle />
          </>
        );

        export default App;
        ```

- Styling a component
    - Uses chains (encadeamento), that means that inside of an element we can keep formating it

        ```jsx
        export const Element = styled.form`

          button {
            width: 210px;
            height: 70px;
            background: 0px 5px 5px 0px;
            border: 0;
            color: #fff;
            font-weight: bold;
        		
        		// in css we would use: button hover { here it already understands
            &:hover { 
              background: ;
            }
          }
        ```

    - we can use library polished: `yarn add polished` that allows us to work with colours including accessibility features. Import it into our styles.ts document: `import { shade } from 'polished';` > to use it in an element, use it as js: ${ }:  `background: ${shade(0.2, '#04d361')};`
    - For accessibility purpose, when we create something clicable it's very important to use buttons or anchors <a>
    - When do I use a <div>? When I need to box elements that changes axis
    - To make a picture totally round use: border-radius: 50%
    - to add icons, can add library react-icons: `yarn add react-icons`
    - How to add styles into an element only when it appears a second time? For example, all the anchors after te first anchor: "a + a" , or, as it is in chain, with "& + a" :

        ```jsx
        a + a {
        }

        // or, when inside of an element, in chain
        a {
            background: #fff;

            & + a {
              margin-top: 16px;
            }

            &:hover {
              transform: translateX(10px);
            }
        }
        ```

- Connecting to API
    1. Create folder services src/services/api.ts 
    2. install axios: `yarn add axios` > add it into app: 

        ```jsx
        import axios from 'axios';

        const api = axios.create({
          baseURL: 'https://api.github.com/',
        });

        export default api;
        ```

    3. Import api into your page index.ts file pages/Dashboard/index/ts: `import api from '../../services/api';`
    4. In the same file import useState to be able to storage data: `import React, { useState } from 'react';`
    5. Create variable to storage it: `const [repositories, setRepositories] =useState([]);` where: repositories  = the state itself , setRepositories = need to use this function eveytime I want to change it , useState([]) = initial state value. This will respect the State and Immutability concepts
    6. function to handle the addition of repositories: 

        ```jsx
        async function handleAddRepository(
            event: FormEvent<HTMLFormElement>, // required in FormEvent documentation
          ): Promise<void> {
            event.preventDefault();
        		
        		// this type is a way to attribute a type to this get
            const response = await api.get<Repository>(`repos/${newRepo}`);

            const repository = response.data;

            setRepositories([...repositories, repository]);
            setNewRepo(''); // cleans input after search
        }
        ```

    7. Full code

        ```jsx
        import React, { useState, FormEvent } from 'react';
        import { FiChevronRight } from 'react-icons/fi';
        import api from '../../services/api';

        import logoImg from '../../assets/logo.svg';

        import { Title, Form, Repositories } from './styles';

        // is created because it is returnin an object
        // type only what you will need, not EVERYTHING that returns from api
        interface Repository {
          full_name: string;
          description: string;
          owner: {
            login: string;
            avatar_url: string;
          };
        }

        const Dashboard: React.FC = () => {
          // repo to store input infos
          const [newRepo, setNewRepo] = useState('');
          // when we create a state that is not standad (string, number...) create an interface
          const [repositories, setRepositories] = useState<Repository[]>([]);

          async function handleAddRepository(
            event: FormEvent<HTMLFormElement>,
          ): Promise<void> {
            /* 
        			What this function has to do?
        			1. have a place to store the input info (what do I have to look for)
        	    2. add a new repo
        	    3. search and get repo from github api
        	    4. save new repo into state
        		*/
            event.preventDefault();

            const response = await api.get<Repository>(`repos/${newRepo}`);

            const repository = response.data;

            setRepositories([...repositories, repository]);
            setNewRepo(''); // cleans input after search
          }

          return (
            <>
              <img src={logoImg} alt="Github Explorer" />
              <Title>Explore repositórios no Github</Title>
        			
        			// what happens when I click the button?
              <Form onSubmit={handleAddRepository}>
                <input
                  value={newRepo}
                  onChange={(e) => setNewRepo(e.target.value)}
                  placeholder="Digite o nome do repositorio"
                />
                <button type="submit">Pesquisar</button>
              </Form>
        			
        			// here is where I show my repository on screen
              <Repositories>
                {repositories.map((repository) => (
                  <a key={repository.full_name} href="test">
                    <img
                      src={repository.owner.avatar_url}
                      alt={repository.owner.login}
                    />
                    <div>
                      <strong>{repository.full_name}</strong>
                      <p>{repository.description}</p>
                    </div>

                    <FiChevronRight size={20} />
                  </a>
                ))}
              </Repositories>
            </>
          );
        };

        export default Dashboard;
        ```

- Errors handling & styling with props

    ## Errors handling

    What happens when an error occurs? When button is pressed without input? Or when a search is done for an invalid repo?

    1. Create a state to store this error src/pages/Dashboard/index/tsx `const [inputError, setInputError] = useState('');`
    2. Inside of the function include a if... this happens... show an error message. In this: if you are not a newRepo, please type what you want in this format:

        ```jsx
        async function handleAddRepository(
            event: FormEvent<HTMLFormElement>,
          ): Promise<void> {
        		event.preventDefault(); // this HAS to come first!!!
            if (!newRepo) {
              setInputError('Type repository author/name');
        			return; // use return just to stop the function
        		}
        ```

    3. What can I do to know if an error was found in requisition? If the repo was not found? You out the request inside of a try/catch: 

        ```jsx
        try {
              const response = await api.get<Repository>(`repos/${newRepo}`);

              const repository = response.data;

              setRepositories([...repositories, repository]);
              setNewRepo(''); // cleans input after search
            } catch (err) {
              setInputError('Error searching for this repository');
            }
          }
        ```

    4. But I need to show this error (setInputError) somewhere... where? We can create a component underneath Form. But this component must only appear when an error is showed. How can we do that? We can use a react way to use if in a simplified way using && that implies that 2nd part will only be executed when 1st part is satisfied: `{inputError && <Error>{inputError}</Error>}` . Remember to import Error from styles and create its style ;)
    5. Styled functions super power: to have access to styled component properties from inside my styles. From Form, that is my styled component, I apply hasError, that will transform a string (inputError) and transform it into a Boolean (true or false). !! is a truthy (has a value) / falsy (empty value) = saying; ! theres's something inside, an error, !! but this is false, than throw an error. O_O crazy logic... 

        ```jsx
        const [inputError, setInputError] = useState('');
        ...

        <Form hasError={Boolean(inputError)} ...

        ***
        /// OR can also write it in this simplified way: 
        <Form hasError={!!inputError} ...
        ```

    6. But hasError needs to be created inside of our styles src/pages/Dashboard/ styles.ts 

        ```jsx
        interface FormProps {
          hasError: boolean;
        }

        ...
        // and pass it into our const Form: 
        export const Form = styled.form<FormProps>`
          margin-top: 40px;
        	...
        ```

    7. But... how do I access this Props?? We can: give it a className, we can add a focus, or, we can do this wild thing: an arrow function to a variable passing props and adding css, as an imported styled components function

        ```jsx
        import styled, { css } from 'styled-components';

        export const Form = styled.form<FormProps>`
        	...
          display: flex;

          input {
            flex: 1;
            ...

            ${(props) =>
              props.hasError &&
              css`
                border-color: #c53030;
              `}
        ```

- Saving search in local storage

    ```jsx
    import React, { useState, FormEvent, useEffect } from 'react';
    ...

    useEffect(() => {
        localStorage.setItem(
          '@GithubExplorer:repositories', // app name I want to show in local storage
          JSON.stringify(repositories), // local storage doesn't take arrays, need to stringfy
        );
      }, [repositories]); // save it into our repository, to follow further changes
    ```

    ![README_Creating%20a%20ReactApp/Screen_Shot_2020-04-24_at_11.21.41.png](README_Creating%20a%20ReactApp/Screen_Shot_2020-04-24_at_11.21.41.png)

    Ok, now we need this to keep being showed in the browser. We can use useEffect for that: 

    ```jsx
    const Dashboard: React.FC = () => {
    	  ...
        // function to keep localstorage repo in browser
        const storageRepositories = localStorage.getItem(
          '@GithubExplorer:repositories', // our app local storage name
        );

        if (storageRepositories) {
          return JSON.parse(storageRepositories); // transform back from stringfy into array
        }
        return [];
      });

      // useEffect allows to start a function (1st param) when this variable is changed (2nd param)
      useEffect(() => {
        localStorage.setItem(
          '@GithubExplorer:repositories',
          JSON.stringify(repositories),
        );
      }, [repositories]);
    ```

- Navigation in between routes without <a> to avoid reload

    To save resources and avoid reloading the page when we navigate to another page, we can use the react function Link (internal links) instead of <a>:

    ```jsx
    import { Link } from 'react-router-dom';
    ...

    <Repositories>
      {repositories.map((repository) => (
    		// change: 
        <a key={repository.full_name} href="test">
    		// to this:
    		<Link key={repository.full_name} to="test">
    		...
    		</Link>
    ```

- Connecting to API

    Fot this we need to connect the web app with database, in this case, github.

    We will need 2 requests: 1 for the repository and 1 specific for the issues, where one is not dependent on another. Therefore, they should be call in the same time.

    To do that we use: { useEffect } from react, that deals with the side effects of things. 

    2 ways to use it and receive both requisitions on the same time.

    #first way, using .then

    ```jsx
    const Repository: React.FunctionComponent = () => {
      const { params } = useRouteMatch<RepositoryParams>();

      useEffect(() => {
        api.get(`repos/${params.repository}`).then((response) => {
          console.log(response.data);
        });

        api.get(`repos/${params.repository}/issues`).then((response) => {
          console.log(response.data);
        });
      }, [params.repository]);

      return (
    ```

    And, although useEffect is a synchronous function, we can use it async as follow

    #2nd way: async function Promise.all()

    ```jsx
    useEffect(() => {
        async function loadData(): Promise<void> {
          const [repository, issues] = await Promise.all([
            api.get(`repos/${params.repository}`),
            api.get(`repos/${params.repository}/issues`)
          ]);

          console.log(repository);
          console.log(issues);
        }

        loadData();
      }, [params.repository]);
    ```

    Now we need to save this inside of my component. For that we  use { useState }

## Notes

- package.json: it is possible to configure it using eject, but it is an UNDO process. As much as possible, try to use build in react structure. Most of the time, no more configuration is needed
- Avoid more than 2 stylization leves. 3 levels may be better to create another component, because it will be TOO much css info
- We can use ? as a "if ternário"