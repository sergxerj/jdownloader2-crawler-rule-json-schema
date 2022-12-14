# json schema definition for validation of jdownloader2 crawler rules

A json schema validator for jdownloader2 linkcrawler rules.

### Usage

- `jd2cr.schema.json` [(direct link)](https://raw.githubusercontent.com/sergxerj/jdownloader2-crawler-rule-json-schema/main/jd2cr.schema.json) for validating a single rule.
- `jd2mcr.schema.json` [(direct link)](https://raw.githubusercontent.com/sergxerj/jdownloader2-crawler-rule-json-schema/main/jd2mcr.schema.json) for validating an array of rules. This is the format that you can "Ctrl+A, Ctrl+V" (in Settings->Advanced Settings->LinkCrawler.linkcrawlerrules) in the current JD2 version as of latest commit.
- included in `.vscode` directory there's a settings.json file that will match and apply `jd2cr.schema.json` to `*.jd2cr`/`*.jd2cr.json` files, and `jd2mcr.schema.json` to `*.jd2mcr`/`*.jd2mcr.json`/`*.linkcrawlerrules.json` files within the project folder. So you can copy this repo and work entirely offline in vscode on your own rules.

### Perks

- The schema files are commented to function as much as possible as documentation themselves, readable to both humans and vscode tooltip/suggestions, though formatted especially for the latter. Specifying the type of expected values for the keys, the rules to which they apply, and examples (which will, depending on vscode config, autoapply on autocompletion). Most of these were taken from [here](https://support.jdownloader.org/Knowledgebase/Article/View/what-are-linkcrawler-rules), some others from reading the forums.
- Keys and values which are specific to a rule type are enforced to be `null` if the current rule type does not apply. Vscode will output warnings and other side-by-side validators (https://jsonschemalint.com, https://www.jsonschemavalidator.net/) will fail to validate the rule(s).
  - OF NOTE: Some implementations might not be the same among all validators. E.g.: VScode **will not** check "HTML RegEx" properties to be valid regex and give any warnings; but https://jsonschemalint.com and https://www.jsonschemavalidator.net/ **will** do this check and validate accordingly. VScode, however, provides autocomplete and documentation tooltipping. Other desktop or online editors may have both, so look around.

### Tips

- To look for urls in the page (for HTML RegEx matching) use View Page Source. If you don't know how to do that, ask Mr. Google "view raw html in {your-browser's-name}", he is your friend ;-).
- Use a regex tool, preferably https://regex101.com/ with the Java 8 flavor, to test your matches. It is *heavily* recommended that you do this as the very first check every time there's anomalous behaviour (such as zero or unwanted matching). Be especially wary of partial url's in the page's source (specifics [here](https://github.com/sergxerj/jdownloader2-crawler-rule-json-schema/blob/d5f0f4e5df14bc2019dd1c989a6713c79278e193/jd2cr.schema.json#L85), read highlighted line all the way to the end. Most browsers do horizontal scrolling with Shift+MouseWheel)
