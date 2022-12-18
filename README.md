## ReactJS, Hooks, Recoil, TDD, Clean Architecture, SOLID


### Source Code

	https://github.com/rmanguinho/clean-react
	
### API Documentation

	http://fordevs.herokuapp.com/api-docs
	
### Snipets

	{
	  "Jest Test": {
		"prefix": ["test"],
		"body": [
		  "describe('', () => {",
		  "  test('', () => {",
		  "",
		  "  })",
		  "})",
		  ""
		],
		"description": "A describe block for Jest"
	  },
	  "React FC": {
		"prefix": ["rfc"],
		"body": [
		  "import React from 'react'",
		  "import Styles from './${TM_FILENAME_BASE}-styles.scss'",
		  "",
		  "const ${TM_FILENAME_BASE/(.*)/${1:/pascalcase}/}: React.FC = () => {",
		  "  return (",
		  "    <div className={Styles.${TM_FILENAME_BASE/([a-z]*)[-]+([a-z]*)/$1${2:/capitalize}/g}Wrap}>",
		  "",
		  "    </div>",
		  "  )",
		  "}",
		  "",
		  "export default ${TM_FILENAME_BASE/(.*)/${1:/pascalcase}/}",
		  ""
		],
		"description": "Boilerplate for React Function Component"
	  }
	}


## Setting dependecies (initial configuration)

### Conventional commits

	URL: https://www.conventionalcommits.org/en/v1.0.0/
	
	a) npm i -D git-commit-msg-linter
	
### TypeScript

	a) npm i -D typescript @types/node
	b) Setup tsconfig.json
	
	
		{
		  "compilerOptions": {
			"target": "es6",
			"lib": [
			  "dom",
			  "dom.iterable",
			  "esnext"
			],
			"esModuleInterop": true,
			"module": "esnext",
			"moduleResolution": "node",
			"jsx": "react",
			"rootDirs": ["src", "tests"],
			"baseUrl": "src",
			"paths": {
			  "@/*": ["*"],
			  "@/tests/*": ["../tests/*"]
			},
			"allowJs": true,
			"resolveJsonModule": true,
			"strictNullChecks": true
		  },
		  "include": ["src", "tests"],
		  "exclude": ["tests/e2e/cypress"]
		}
	
	
### Linter

	a) npm i -D eslint eslint-config-standard-with-typescript eslint-plugin-import 
	eslint-plugin-node eslint-plugin-promise eslint-plugin-standard @typescript-eslint/eslint-plugi
	
	b) Setup .eslintrc.json
	
		{
		  "extends": "standard-with-typescript",
		  "parserOptions": {
			"project": "./tsconfig.json"
		  },
		  "rules": {
			"@typescript-eslint/consistent-type-definitions": "off",
			"@typescript-eslint/strict-boolean-expressions": "off"
		  }
		}
	
	c) Setup .eslintignore
	
		node_modules
		.vscode
	
### Avoiding commits with issues

	a) npm i -D lint-staged husky
	
	b) Setup .lintstagedrc.json
	
		{
		  "*.{ts,tsx}": [
			"eslint 'src/**' --fix"
		  ]
		}
		
	c) Setup .huskyrc.json
	
		{
		  "hooks": {
			"pre-commit": "lint-staged"
		  }
		}
		
### Jest

	a) npm i -D jest @types/jest ts-jest
	
	b) Setup jest.config.js
	
		module.exports = {
		  roots: ['<rootDir>/src'],
		  collectCoverageFrom: [
			'<rootDir>/src/**/*.{ts,tsx}'
		  ],
		  coverageDirectory: 'coverage',
		  testEnvironment: 'node',
		  transform: {
			'.+\\.ts$': 'ts-jest'
		  }
		}

	
	
	
	