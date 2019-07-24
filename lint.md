# lint リント sublime text 

## eslint

1. $ npm install -g eslint
2. STでSublimeLinter をインストール
3. STでSublimeLinter-contrib-eslint をインストール
4. STでSublimeLinter-contrib-pug-lint をインストール
5. STでPreferences -> Package Settings -> SublimeLinter -> Settings User

下記を記述
```json
// SublimeLinter Settings - User
{
  "linters": {
    "eslint":
    {
      "@disable": false,
      "args":
      [
        "--config",
        "/path/to/lint/.eslintrc.json",
      ],
      "excludes": []
    },
    "puglint":
    {
      "@disable": false,
      "args":
      [
        "--config",
        "/path/to/.pug-lintrc"
      ],
      "excludes": []
    }
  },
  "paths": {
      "linux": [],
      "osx": [],
      "windows": []
  },
  "styles": [
    {
      "mark_style": "outline",
      "priority": 1,
      "scope": "region.purplish markup.changed.sublime_linter markup.warning.sublime_linter",
      "icon": "warning",
      "types": [
          "warning"
      ]

    },
    {
      "mark_style": "outline",
      "priority": 1,
      "scope": "region.redish markup.deleted.sublime_linter markup.error.sublime_linter",
      "icon": "error",
      "types": [
          "error"
      ]
    }


  ],
  "syntax_map": {
  },
  "debug": false

}
```


3. /path/to/にlint ディレクトリを作る

4. その中に.eslintrc.jsonを用意
```json
{
    "env": {
        "browser": true,
        "node": true,
        "jquery": true,
        "es6": true
    },
    "extends": "eslint:recommended",
    "parser": "babel-eslint",
    "parserOptions": {
        "ecmaVersion": 6,
        "sourceType": "module"
    },
    "rules": {
        "linebreak-style": [
            "error",
            "unix"
        ],
        "quotes": [
            "warn",
            "double"
        ],
        "semi": [
            "error",
            "always"
        ],
        "no-console": [
            "warn",
            {
                "allow": [
                    "warn", "error"
                ]
            }
        ],
        "no-unused-vars": [
            "warn"
        ]
    },
    "plugins": [
    ]
}
```


5. lint内で
```bash
$ npm init
$ npm i --save babel-eslint
$ npm i -g eslint #←いらない？
```

6. sublime text 再起動


## 補足

* SublimeTextの表示設定は`SublimeLinter.sublime-settings`に書く
* lint自体の設定は/path/to/lint/.eslintrc.jsoに書く
    * babel-eslintは.eslintrc.jsonから見える位置に置く必要があるので、同じディレクトリでnpm installをする必要があるはず


tags: lint, リント, jslint, jshint, eslint