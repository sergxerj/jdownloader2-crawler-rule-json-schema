# json schema definition for validation of jdownloader2 crawler rules

A json schema validator for jdownloader2 linkcrawler rules.

### Usage

- `jd2cr.schema.json` [(direct link)](https://raw.githubusercontent.com/sergxerj/jdownloader2-crawler-rule-json-schema/main/jd2cr.schema.json) for validating a single rule.
- `jd2mcr.schema.json` [(direct link)](https://raw.githubusercontent.com/sergxerj/jdownloader2-crawler-rule-json-schema/main/jd2mcr.schema.json) for validating an array of rules. This is the format that you can "Ctrl+A, Ctrl+V" in the current JD2 version as of latest commit.
- included in `.vscode` directory there's a settings.json file that will match and apply `jd2cr.schema.json` to `*.jd2cr.json` files, and `jd2mcr.schema.json` to `*.jd2mcr.json` files within the project folder. So you can clone this repo and work entirely offline in vscode.

### Perks

- The schema files are commented to function as much as possible as documentation themselves, readable to both humans and vscode tooltip/suggestions, though formatted especially for the latter. Specifying the type of expected values for the keys, the rules to which they apply, and examples (which will, depending on vscode config, autoapply on autocompletion). Most of these were taken from [here](https://support.jdownloader.org/Knowledgebase/Article/View/what-are-linkcrawler-rules), some others from reading the forums.
- Keys and values which are specific to a rule type are enforced to be `null` if the current rule type does not apply. Vscode will output warnings and other side-by-side validators (https://jsonschemalint.com, https://www.jsonschemavalidator.net/) will fail to validate the rule(s).

### Tips

- Use a regex tool, preferably https://regex101.com/ with the Java 8 engine to test your matches.
- To look for urls in the page (for HTML RegEx matching) use View Page Source. If you don't know how to do that, ask Mr. Google "view raw html in {your-browser's-name}", he is your friend ;-).
