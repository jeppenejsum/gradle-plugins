# Gradle Plugins

These are a variety of plugins that I wrote for [Gradle](http://gradle.org) and figured I'd share with the world.

## ClassLoaders

### Description

Provides two methods on the `project` object to work with configuration classloaders:
  * `classLoaderFor(configName)`&mdash;Provides a `java.lang.ClassLoader` consisting of all of the classes for a configuration.
  * `classFor(configName, className)`&mdash;Looks up the class for name `className` using the class loader for config `configName`.

### Usage
    usePlugin(ClassLoadersPlugin)

### Example
    task(foo) << {
      project.classFor(bar, "my.app.Main").main()
    }

## ExecPlugin

### Description

Provides methods `exec(cmd)` and `exec(cmd, baseDir)` on the project to execute shell commands.  If the command does not return 0, the build will fail.

### Usage
    usePlugin(ExecPlugin)

### Example
    project.exec("ls -al", project.buildDir)

# Installation

To use these plugins, simply drop the `buildSrc` file into the root of your project (right beside your `build.gradle`).  That's all it takes!

Unfortunately, there's no plugin ecosystem or `svn externals` equivalent for git (if I'm wrong, please correct me!), so you're pretty much [SOL](http://www.urbandictionary.com/define.php?term=shit%20out%20of%20luck&defid=1646062) for sane maintenance.

# Author and Origin

These plugins were written by [Robert Fischer](http://smokejumperit.com/).  They are published at [GitHub:RobertFischer/gradle-plugins](http://github.com/RobertFischer/gradle-plugins).

# License

All these plugins are licensed under the [Creative Commons — CC0 1.0 Universal](http://creativecommons.org/publicdomain/zero/1.0/) license, with no warranty (expressed or implied) for any purpose.