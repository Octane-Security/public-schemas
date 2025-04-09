# Octane public schemas


## OctaneRC

The OctaneRC configuration file allows you to customize how Octane processes your project. Create a `.octanerc.json` file in the root of your repository to configure Octane's behavior.

### Configuration

The `.octanerc.json` file should be in JSON format with the following structure:

```json
{
  "$schema": "https://raw.githubusercontent.com/Octane-Security/public-schemas/refs/heads/main/octanerc.json",     
  "pathsToIgnore": ["**/path/to/ignore/**", "another/path/to/ignore"],
  "pathsToAnalyze": ["**/path/to/analyze/**", "specific/file/to/analyze.js"]
}
```

### Options

#### `pathsToIgnore` (Blacklist)

Use the `pathsToIgnore` property to specify files or directories that should be excluded from Octane processing. This accepts an array of glob patterns.

Example:
```json
{
  "$schema": "https://raw.githubusercontent.com/Octane-Security/public-schemas/refs/heads/main/octanerc.json",     
  "pathsToIgnore": [
    "**/src/dev/**/*"
}
```

#### `pathsToAnalyze` (Whitelist)
E
Use the `pathsToAnalyze` property to explicitly define which files or directories should be processed by Octane. When the `pathsToAnalyze` property is defined, Octane will only process the specified paths. This accepts an array of glob patterns.

Example:
```json
{
  "$schema": "https://raw.githubusercontent.com/Octane-Security/public-schemas/refs/heads/main/octanerc.json",
  "pathsToAnalyze": [
    "**/packages/eth-contracts/**/*"
  ]
}
```

### Priority

When both `pathsToIgnore` and `pathsToAnalyze` are specified, the `pathsToIgnore` patterns are applied after the `pathsToAnalyze` patterns. This means that even if a file matches an `pathsToAnalyze` pattern, it will be ignored if it also matches an `pathsToIgnore` pattern.

