# Espanso Config Schema

This schema is used to validate an [Espanso][0] [configuration file][1]. At the time of writing it only handles the top-level properties. This is due to the complexity of the `matches` property which can handle all kinds of various cases.

## How To Use

In order to use this schema, you have to add it to VSCode in one of two ways:

1. Add it to your User settings so it's available across all your VSCode instances.
2. Add it to the workspace/folder settings so it's available only for the workspace/folder you're currently working in.

Either way, you'll need to open your preferences in JSON form:

![JSON-Settings](JSON-Settings-Cropped.png)

Once you have that open, you'll need to add the following setting:

```json
"yaml.schemas": {
  "https://raw.githubusercontent.com/4lch4-Industries/JSON-Schemas/main/Espanso-Config.json": [
    "default.yml",
    "default.yaml",
    "package.yml",
    "package.yaml",
    "user/**/*.yml",
    "user/**/*.yaml",
    "packages/**/*.yaml",
    "packages/**/*.yml"
  ]
}
```

Now, let's break this down a bit so you understand what this is doing:

1. `yaml.schemas`
   - Defines any custom schema objects that aren't in the [SchemaStore][2], such as this one. Down the road I would like for this schema to be added to the SchemaStore, but for now this will have to do.
2. **Line 2** (<https://raw.githubusercontent.com/...>)
   - This line defines the URL where the custom schema can be found.
3. **Lines 3-10** (`*.yml/yaml`)
   - This line defines the files that the schema should be applied to.
   - The standard Espanso config file is `default.yml` or `default.yaml`.
   - Packages can either be nested in the `user` directory, or within a `packages` directory.

At this point, you can reload VS Code and open an Espanso config file to see it in action:




[0]: https://espanso.org/
[1]: https://espanso.org/docs/configuration/
[2]: https://www.schemastore.org/json/
