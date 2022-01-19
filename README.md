# napari-plugin-action

this is a WIP github action that you can use to test a couple things about your plugin.

Currently this likely only works for **first generation** plugins.  (npe2 coming later)

to use, add something like this to your github action

```yaml
name: Test composite action

on: [push]

jobs:
  build-linux:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - uses: tlambert03/napari-plugin-action@main
      with:
        package_name: <your-package-name>
```

-----

Currently checks:

1. That your plugin declares a proper napari plugin entry point
2. Test that your plugin is detected by the plugin engine
3. Test that any declared dock widgets can be instantiated
4. Test that your package doesn't result in multiple Qt backends getting installed
5. (Currently off) - Test that your package doesn't abuse the npe1 entry points
   (by declaring an entry point that doesn't actual offer any hooks).  This is a
   potential sign of plugin abuse.
