# RepoSense - Guide to Setup Standalone Configuration
### Quick Start
1. Add [_reposense/config.json](../_reposense/config.json) to the root of your repository.
1. Fill it up with author information, such as the GitHub Id, Display Name (Optional), [Author Names](UserGuide.md#git-author-name)  (Optional), [Ignore Glob List](UserGuide.md#csv-config-file) (Optional).

### Detailed explanation of the structure of repo-config.json

#### Typical format of repo-config.json
```
{
  "ignoreGlobList": ["about-us/**", "**index.html"],    
  "formats": ["html", "css"],
  "ignoreCommitList": ["12345abc", "67890def"],
  "authors":
  [
    {
      "githubId": "alice",
      "displayName": "Alice T.",
      "authorNames": ["AT", "A"],
      "ignoreGlobList": ["**.css"]
    },
    {
      "githubId": "bob"
    }
  ]
}
```
#### Line-by-line explanation
```
// Repository level configuration
"ignoreGlobList": ["about-us/**", "**index.html"]  <-- Repository level's list of folder or file formats to
                                                       ignore.

// First Author
"formats": ["html", "css"]                         <-- Repository level's file formats to analyse.      
                                                       If not provided, the following file formats will be used.
                                                       adoc, cs, css, fxml, gradle, html, java, js, json, jsp,
                                                       md, py, tag, xml.
                                                       
"ignoreCommitList": ["12345abc", "67890def"]       <-- The list of commits to ignore during analysis. For accurate
                                                       results, the commits should be provided with their full hash.

"ignoreGlobList": ["**.css"]                       <-- Author level's ignoreGlobList adds on to the Repository
                                                       level's. Thus, the actual ignoreGlobList for alice would
                                                       contain css, index.html and about-us.

// Second Author
"githubId": "bob"                                  <-- Only githubId is mandatory.
                                                       Optional information can be left out to prevent clutter.
```
### Verify your standalone configuration
Download the latest executable Jar from our [release](https://github.com/reposense/RepoSense/releases/latest).

#### Using github repository url location(s)
1. Run RepoSense using the url link to your repository i.e. `https://github.com/reposense/RepoSense.git`. RepoSense will run the analysis on the `master` branch and use the authors provided in your repository for analysis.

```
java -jar RepoSense.jar -repos https://github.com/reposense/RepoSense.git
```