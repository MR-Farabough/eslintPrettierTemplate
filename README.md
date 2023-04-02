# How to install ESLINT & PRETTIER

> This is to follow a general styling.
> If you want other options select the ones that apply to you

# prerequisite

Download the extensions `prettier` and `eslint` in VSCODE

# Starting with ESLINT

Create package.json

- `npm init --yes`

Install ESLINT

- `npm install eslint --save-dev`

Initialize ESLINT Config

- `./node_modules/.bin/eslint --init`

Select the following options (or whichever ones apply)

<pre>? How would you like to use ESLint? …
    To check syntax only
    To check syntax and find problems
    ❯ To check syntax, find problems, and enforce code style

What type of modules does your project use? …
    JavaScript modules (import/export)
    ❯ CommonJS (require/exports)
    None of these

? Which framework does your project use? …
    React
    Vue.js
    ❯ None of these

? Does your project use TypeScript?
    › No / Yes

? Where does your code run? …
    ✔ Browser
    Node

✔ How would you like to define a style for your project? …
    ❯ Use a popular style guide
    Answer questions about your style
    Inspect your JavaScript file(s)

? What format do you want your config file to be in? …
    JavaScript
    YAML
    ❯ JSON

? Would you like to install them now with npm?
    No / › Yes
</pre>

Open the command palette `CTRL + SHIFT + P` to open `Preferences: Open Workspace Settings (JSON)`

<pre>{
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "eslint.validate": ["javascript"]
}</pre>

> What do the different "variables" mean?

- error - produces a red underline
- warn - will produce a yellow underline
- off - will not display anything.

Open `.eslintrc.json`

<pre>{
    "env": {
        "browser": true,
        "commonjs": true,
        "es2021": true
    },
    "extends": [
        "airbnb-base"
    ],
    "parserOptions": {
        "ecmaVersion": 12
    },
    "rules" : {
    "no-console": "off",
    "quotes": [
        "error",
        "single"
    ]
}
</pre>

This removes the error messages from your console.log statements
As well as makes strings 'single quotes'

# Install Prettier

Install Prettier

- `npm i --save-dev --save-exact prettier`

To adjust settings in prettier

- open settings and search `prettier`

Make sure format on save is on

- open settings and search `formatonsave` and check the box

> In order to ignore files for prettier. Create a `.prettierignore`
> Example of popular use cases

<pre>
node_modules
.vscode
.eslintrc.json
package-lock.json
package.json
</pre>

If you want to change options in prettier create a `.prettierrc` file

<pre>
{
    "semi": true,
    "overrides": [
        {
            "files": "*.ts",
            "options": {
                "semi": false
            }
        }
    ]
}
</pre>

# IMPORTANT

To make sure `ESLINT` and `PRETTIER` work together

- `npm i --save-dev eslint-config-prettier`

The above will turn off any ESLINT feature that conflicts with prettier

> Make sure to add "prettier" to the end of your `extends` attirbute in `.eslintrc.json` file
> Example

<pre>{
    "env": {
        "browser": true,
        "commonjs": true,
        "es2021": true
    },
    "extends": [
        "airbnb-base",
        "prettier"
    ],
    "parserOptions": {
        "ecmaVersion": 12
    },
    "rules" : {
        "no-console": "off",
        "quotes": [
            "error",
            "single"
        ]
    }
}
</pre>
