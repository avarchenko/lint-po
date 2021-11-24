### lint-po

A simple gettext .po linter to check for mangled variable names in translations.


#### Features

* reads utf-8 encoded *.po files
* skips `msgid/msgstr` pairs where either value is unset
* compares original/translation pairs for common interpolation markars:
  * supports `{name}`, `{123}`, `<123>`, `</123>`, `<123/>`, `%(name)s`
  * ensures both messages use the same set of variables - no renames, no removals, no additions
* supports Github Actions error reporting syntax (when `env.GITHUB_ACTIONS` is set)


#### Example usage

```sh
$ lint-po locale/*.po

Difference between msgid="Hello {name}" and msgstr="Bonjour {nom}":
  Missing from msgstr: {name}
  Unexpected in msgstr: {nom}
  at problem.po:2
```
