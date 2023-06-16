.. 8080.md

.. _supported-plugins:

# Supported plugins

The following plugins are currently supported by Snapcraft. See [Snapcraft plugins](snapcraft-plugins.md) for more details in how they're used, and to create your own, see [Writing local plugins](writing-local-plugins.md).

> ⓘ From Snapcraft 4.0 onwards, if the working directory contains a Snapcraft project, the default behaviour is to show only the plugins available for either its specified base or the latest available supported base (currently  `core22` ). See [Base snaps](base-snaps.md) for more details.

## Programming languages

<h3 id='supported-plugins-heading--go'>Go</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [go](the-go-plugin.md) | integrates projects written in Go and using the *go get* package installer  | [core22](/t/the-go-plugin/8505#supported-plugins-heading--core22) <br /> [core20](/t/the-go-plugin/8505#supported-plugins-heading--core20) <br /> [core18](/t/the-go-plugin/8505#supported-plugins-heading--core18) |
 [godeps](the-godeps-plugin.md) | integrates projects written in Go and using the *godep* dependency tool | [core18](the-godeps-plugin.md) |

<h3 id='supported-plugins-heading--java'>Java</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [ant](the-ant-plugin.md) | Ant build system integration, commonly used by Java projects | core22</br>core20</br>core18 |
| [gradle](the-gradle-plugin.md) | integrate projects built using the Gradle build tool with your snaps | core18 |
| [maven](the-maven-plugin.md) | build system integration with *Maven*, commonly used by Java projects  | core22</br>core18 |

<h3 id='supported-plugins-heading--javascript'>Node.js/JavaScript</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [gulp](the-gulp-plugin.md) |  build parts from projects using the gulp.js streaming build system | core18 |
| [npm](the-npm-plugin.md) | create parts that use Node.js and/or the JavaScript package manager, npm | [core22](/t/the-npm-plugin/17591#supported-plugins-heading--core22) <br /> [core20](/t/the-npm-plugin/17591#supported-plugins-heading--core20) |
| [nodejs](the-nodejs-plugin.md) | create parts that use Node.js and/or the JavaScript package manager, npm | [core18](/t/the-nodejs-plugin/8514#supported-plugins-heading--core18) |

<h3 id='supported-plugins-heading--python'>Python</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [conda](the-conda-plugin.md) | used for parts incorporating the Conda open source package manager system | [core22](/t/the-conda-plugin/12530#supported-plugins-heading--core22) <br /> [core20](/t/the-conda-plugin/12530#supported-plugins-heading--core20) <br /> [core18](/t/the-conda-plugin/12530#supported-plugins-heading--core18)|
| [python](the-python-plugin.md) | used for parts incorporating projects written with Python 2 or Python 3 |  [core22](/t/the-python-plugin/8529#supported-plugins-heading--core22) <br /> [core20](/t/the-python-plugin/8529#supported-plugins-heading--core20) <br /> [core18](/t/the-python-plugin/8529#supported-plugins-heading--core18) |

<h3 id='supported-plugins-heading--other'>Other languages</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [crystal](the-crystal-plugin.md) | build parts from projects written in the Ruby-like Crystal language | [core20](/t/the-crystal-plugin/12527#supported-plugins-heading--core20) <br /> [core18]( /t/the-crystal-plugin/12527#supported-plugins-heading--core18) |
| [dotnet](the-dotnet-plugin.md) | integrates with the Microsoft's .NET SDK to build core runtime parts  | [core22](/t/the-dotnet-plugin/8584#supported-plugins-heading--core22) <br /> [core18](/t/the-dotnet-plugin/8584#supported-plugins-heading--core18) |
| [flutter](the-flutter-plugin.md) | easily build and deploy parts for the expressive Flutter UI toolkit  | [core22](/t/the-flutter-plugin/18746#supported-plugins-heading--core22)</br>[core18](/t/the-flutter-plugin/18746#supported-plugins-heading--core18) |
| [ruby](the-ruby-plugin.md) | built parts from projects written in Ruby and its Gemfile dependency bundler | core18 |
| [rust](the-rust-plugin.md) | build parts from projects written in Rust and using Cargo for dependency management  | [core22](/t/the-rust-plugin/8588#supported-plugins-heading--core22) <br /> [core20](/t/the-rust-plugin/8588#supported-plugins-heading--core20) <br /> [core18](/t/the-rust-plugin/8588#supported-plugins-heading--core18) |

<h2 id='supported-plugins-heading--build-tools'>Build tools</h2>

| Plugin name |  Description | Base support |
|--|--|--|
| [autotools](the-autotools-plugin.md) | integrates projects that use the common Autotools suite with your snaps |  [core22](/t/the-autotools-plugin/8616#supported-plugins-heading--core22) <br /> [core20](/t/the-autotools-plugin/8616#supported-plugins-heading--core20) <br /> [core18](/t/the-autotools-plugin/8616#supported-plugins-heading--core18)
| [cmake](the-cmake-plugin.md) | integrates projects that use the common CMake build tool with your snaps  | [core22](/t/the-cmake-plugin/8621#supported-plugins-heading--core22) <br /> [core20](/t/the-cmake-plugin/8621#supported-plugins-heading--core20) <br /> [core18](/t/the-cmake-plugin/8621#supported-plugins-heading--core18) |
| [make](the-make-plugin.md) | integrates projects using the commonly found *make* build system | [core22](/t/the-make-plugin/8622#supported-plugins-heading--core22) <br /> [core20](/t/the-make-plugin/8622#supported-plugins-heading--core20) <br /> [core18](/t/the-make-plugin/8622#supported-plugins-heading--core18)
| [meson](the-meson-plugin.md) | integrate projects build using the Meson build system into your snap | [core22](/t/the-meson-plugin/8623#supported-plugins-heading--core22) <br /> [core20](/t/the-meson-plugin/8623#supported-plugins-heading--core20) <br /> [core18](/t/the-meson-plugin/8623#supported-plugins-heading--core18) |
| [qmake](the-qmake-plugin.md) | integrates projects using the qmake build tool, commonly by *Qt*-based projects | [core20](/t/the-qmake-plugin/8628#supported-plugins-heading--core20) <br /> [core18](/t/the-qmake-plugin/8628#supported-plugins-heading--core18) |
| [scons](the-scons-plugin.md) | integrates projects that use the SCons construction tool | core22</br>core18 |
| [waf](the-waf-plugin.md) | integrate projects using the Waf build automation tool | core18

## Platforms

### Linux kernel

| Plugin name |  Description | Base support |
|--|--|--|
| [kbuild](the-kbuild-plugin.md) | build parts that use the Linux kernel build system (kBuild) | core18 |
| [kernel](the-kernel-plugin.md) | derived from the *kbuild* plugin and used to build your own kernel | core18 |

### Robot Operating System (ROS)

| Plugin name |  Description | Base support |
|--|--|--|
| [ament](the-ament-plugin.md) | uses ament_cmake to build parts for version 2 of the Robot Operating System (ROS 2) | core18 |
| [catkin](the-catkin-plugin.md) | build catkin-based parts, typically used with version 1 of the Robot Operating System (ROS 1) | [core20](/t/the-catkin-plugin/8644#supported-plugins-heading--core20) <br /> [core18](/t/the-catkin-plugin/8644#supported-plugins-heading--core18) |
| [catkin-tools](the-catkin-tools-plugin.md) | alternative method for building projects using version 1 of the Robot Operating System (ROS 1)   | [core20](/t/the-catkin-tools-plugin/8645#supported-plugins-heading--core20) <br /> [core18](/t/the-catkin-tools-plugin/8645#supported-plugins-heading--core18) |
| [colcon](the-colcon-plugin.md) | build colcon-based parts, typically used with version 2 of the Robot Operating System (ROS 2)  | [core22](/t/the-colcon-plugin/11895#supported-plugins-heading--core22) <br />[core20](/t/the-colcon-plugin/11895#supported-plugins-heading--core20) <br /> [core18](/t/the-colcon-plugin/11895#supported-plugins-heading--core18) |

## Tools

| Plugin name |  Description | Base support |
|--|--|--|
| [dump](the-dump-plugin.md) | simply dumps the contents from the specified source | core22 <br /> core20 <br /> core18 |
| [nil](the-nil-plugin.md) | useful for parts with no source to import | core22 <br /> core20 <br /> core18 |
| [plainbox-provider](the-plainbox-provider-plugin.md) | create parts containing a Plainbox test collection known as a *provider*  | core18 |8