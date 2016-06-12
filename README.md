# gitbook-plugin-git-author

This is a plugin for automatically adding author and timestamp to each gitbook article, including creator and last modified user from git commits

## Usage

### Recommended Environments

- Node.js 4.0+
- npm 3.0+
- gitbook 3.0+

### install

```sh
npm i -D gitbook-plugin-git-author
```

### book.json

```js
{
    "plugins": ["git-author"]
    "pluginsConfig": {
          "git-author":{
              "position": "bottom",
              "modifyTpl": "Last modified by {user} {timeStamp}",
              "createTpl": "Created by {user} {timeStamp}",
              "timeStampFormat": "YYYY-MM-DD HH:mm:ss"
          }
    }
}
```

## Example

`README.md` file

Be sure to commit this file to git repository firstly.

```markdown
# Title of the Article

content
```

### Output

```html
<h1>Title of the Article</h1>

<p>content</p>

<div class="git-author-container git-author-bottom">
    <div class="modified">Last modified by someone 2016-06-06 06:06:06</div>
    <div class="created">Created by someone 2016-06-06 06:06:06</div>
</div>
```

## Options

### `position`

default: `bottom`

git-author content position in the article. `top` or `bottom` 

this will add a `git-author-{position}` className to `git-author-container`

### `createTpl`  `modifyTpl`

You can use `{user}` `{timeStamp}` as placeholder for username and timeStamp

default: 

createTpl: `Created by {user} {timeStamp}`
modifyTpl: `Last modified by {user} {timeStamp}`

You may disable one of them by set it to a FALSY value.

e.g

```
"createTpl": false
```

### `timeStampFormat`

default: `YYYY-MM-DD HH:mm:ss`

use [moment](https://www.npmjs.com/package/moment) to process timeStamp


## custom styles

change default style by add a custom css file to your gitbook

`book.json`

```js
{
    "styles": {
        "website": "./website.css"
    }
}
```

`website.css`

```
.git-author-container {
    font-size: 85%;
}

.git-author-top {
    float: none;
}
```


