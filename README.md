# metalsmith-reading-time

**⚠️ This repistory has been moved to [metalsmith-plugins](https://github.com/emmercm/metalsmith-plugins/tree/main/packages/metalsmith-reading-time). ⚠️**

[![npm Version](https://badgen.net/npm/v/metalsmith-reading-time?icon=npm)](https://www.npmjs.com/package/metalsmith-reading-time)
[![npm Weekly Downloads](https://badgen.net/npm/dw/metalsmith-reading-time)](https://www.npmjs.com/package/metalsmith-reading-time)

[![Known Vulnerabilities](https://snyk.io/test/npm/metalsmith-reading-time/badge.svg)](https://snyk.io/test/npm/metalsmith-reading-time)
[![Test Coverage](https://badgen.net/codecov/c/github/emmercm/metalsmith-reading-time/master?icon=codecov)](https://codecov.io/gh/emmercm/metalsmith-reading-time)
[![Maintainability](https://badgen.net/codeclimate/maintainability/emmercm/metalsmith-reading-time?icon=codeclimate)](https://codeclimate.com/github/emmercm/metalsmith-reading-time/maintainability)

[![GitHub](https://badgen.net/badge/emmercm/metalsmith-reading-time/purple?icon=github)](https://github.com/emmercm/metalsmith-reading-time)
[![License](https://badgen.net/github/license/emmercm/metalsmith-reading-time?color=grey)](https://github.com/emmercm/metalsmith-reading-time/blob/master/LICENSE)

A Metalsmith plugin to estimate pages' reading times.

## Installation

```bash
npm install --save metalsmith-reading-time
```

## JavaScript Usage

```javascript
const Metalsmith  = require('metalsmith');
const readingTime = require('metalsmith-reading-time');

Metalsmith(__dirname)
    .use(readingTime({
        // options here
    }))
    .build((err) => {
        if (err) {
            throw err;
        }
    });
```

## File metadata

This plugin adds a metadata field named `readingTime` to each file which can be used with templating engines, such as with [`handlebars`](https://www.npmjs.com/package/handlebars):

```handlebars
Reading time: {{ readingTime }}

The rest of the page content.
```

Reading time will be reported in minutes in the form "# min read" per [`reading-time`](https://www.npmjs.com/package/reading-time).

## Options

### `pattern` (optional)

Type: `string` Default: `**/*`

A [`micromatch`](https://www.npmjs.com/package/micromatch) glob pattern to find input files.

### `stripHtml` (optional)

Type: `boolean` Default: `true`

Whether to strip HTML tags from content before evaluating the reading time or not.

### `replacements` (optional)

type: `(string|RegExp)[][]` Default: `[]`

A list of tuples fed to `String.replace()` to get rid of meaningless content before evaluating the reading time.

### `readingTime` (optional)

Type: `object` Default: `{}`

An object of [`reading-time`](https://www.npmjs.com/package/reading-time) options, example:

```json
{
  "readingTime": {
    "wordsPerMinute": 200
  }
}
```

## Changelog

[Changelog](./CHANGELOG.md)
