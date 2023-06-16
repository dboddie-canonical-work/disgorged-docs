.. 8080.md

.. _supported-plugins:

# Supported plugins

The following plugins are currently supported by Snapcraft. See [Snapcraft plugins](/t/snapcraft-plugins/4284) for more details in how they're used, and to create your own, see [Writing local plugins](/t/writing-local-plugins/5125).

> ⓘ From Snapcraft 4.0 onwards, if the working directory contains a Snapcraft project, the default behaviour is to show only the plugins available for either its specified base or the latest available supported base (currently  `core22` ). See [Base snaps](/t/base-snaps/11198) for more details.

## Programming languages

<h3 id='heading--go'>Go</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [go](/t/the-go-plugin/8505) | integrates projects written in Go and using the *go get* package installer  | [core22](/t/the-go-plugin/8505#heading--core22) <br /> [core20](/t/the-go-plugin/8505#heading--core20) <br /> [core18](/t/the-go-plugin/8505#heading--core18) |
 [godeps](/t/the-godeps-plugin/8506) | integrates projects written in Go and using the *godep* dependency tool | [core18](/t/the-godeps-plugin/8506) |

<h3 id='heading--java'>Java</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [ant](/t/the-ant-plugin/8507) | Ant build system integration, commonly used by Java projects | core22</br>core20</br>core18 |
| [gradle](/t/the-gradle-plugin/5390) | integrate projects built using the Gradle build tool with your snaps | core18 |
| [maven](/t/the-maven-plugin/4282) | build system integration with *Maven*, commonly used by Java projects  | core22</br>core18 |

<h3 id='heading--javascript'>Node.js/JavaScript</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [gulp](/t/the-gulp-plugin/8511) |  build parts from projects using the gulp.js streaming build system | core18 |
| [npm](/t/the-npm-plugin/17591) | create parts that use Node.js and/or the JavaScript package manager, npm | [core22](/t/the-npm-plugin/17591#heading--core22) <br /> [core20](/t/the-npm-plugin/17591#heading--core20) |
| [nodejs](/t/the-nodejs-plugin/8514) | create parts that use Node.js and/or the JavaScript package manager, npm | [core18](/t/the-nodejs-plugin/8514#heading--core18) |

<h3 id='heading--python'>Python</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [conda](/t/the-conda-plugin/12530) | used for parts incorporating the Conda open source package manager system | [core22](/t/the-conda-plugin/12530#heading--core22) <br /> [core20](/t/the-conda-plugin/12530#heading--core20) <br /> [core18](/t/the-conda-plugin/12530#heading--core18)|
| [python](/t/the-python-plugin/8529) | used for parts incorporating projects written with Python 2 or Python 3 |  [core22](/t/the-python-plugin/8529#heading--core22) <br /> [core20](/t/the-python-plugin/8529#heading--core20) <br /> [core18](/t/the-python-plugin/8529#heading--core18) |

<h3 id='heading--other'>Other languages</h3>

| Plugin name |  Description | Base support |
|--|--|--|
| [crystal](/t/the-crystal-plugin/12527) | build parts from projects written in the Ruby-like Crystal language | [core20](/t/the-crystal-plugin/12527#heading--core20) <br /> [core18]( /t/the-crystal-plugin/12527#heading--core18) |
| [dotnet](/t/the-dotnet-plugin/8584) | integrates with the Microsoft's .NET SDK to build core runtime parts  | [core22](/t/the-dotnet-plugin/8584#heading--core22) <br /> [core18](/t/the-dotnet-plugin/8584#heading--core18) |
| [flutter](/t/the-flutter-plugin/18746) | easily build and deploy parts for the expressive Flutter UI toolkit  | [core22](/t/the-flutter-plugin/18746#heading--core22)</br>[core18](/t/the-flutter-plugin/18746#heading--core18) |
| [ruby](/t/the-ruby-plugin/8587) | built parts from projects written in Ruby and its Gemfile dependency bundler | core18 |
| [rust](/t/the-rust-plugin/8588) | build parts from projects written in Rust and using Cargo for dependency management  | [core22](/t/the-rust-plugin/8588#heading--core22) <br /> [core20](/t/the-rust-plugin/8588#heading--core20) <br /> [core18](/t/the-rust-plugin/8588#heading--core18) |

<h2 id='heading--build-tools'>Build tools</h2>

| Plugin name |  Description | Base support |
|--|--|--|
| [autotools](/t/the-autotools-plugin/8616) | integrates projects that use the common Autotools suite with your snaps |  [core22](/t/the-autotools-plugin/8616#heading--core22) <br /> [core20](/t/the-autotools-plugin/8616#heading--core20) <br /> [core18](/t/the-autotools-plugin/8616#heading--core18)
| [cmake](/t/the-cmake-plugin/8621) | integrates projects that use the common CMake build tool with your snaps  | [core22](/t/the-cmake-plugin/8621#heading--core22) <br /> [core20](/t/the-cmake-plugin/8621#heading--core20) <br /> [core18](/t/the-cmake-plugin/8621#heading--core18) |
| [make](/t/the-make-plugin/8622) | integrates projects using the commonly found *make* build system | [core22](/t/the-make-plugin/8622#heading--core22) <br /> [core20](/t/the-make-plugin/8622#heading--core20) <br /> [core18](/t/the-make-plugin/8622#heading--core18)
| [meson](/t/the-meson-plugin/8623) | integrate projects build using the Meson build system into your snap | [core22](/t/the-meson-plugin/8623#heading--core22) <br /> [core20](/t/the-meson-plugin/8623#heading--core20) <br /> [core18](/t/the-meson-plugin/8623#heading--core18) |
| [qmake](/t/the-qmake-plugin/8628) | integrates projects using the qmake build tool, commonly by *Qt*-based projects | [core20](/t/the-qmake-plugin/8628#heading--core20) <br /> [core18](/t/the-qmake-plugin/8628#heading--core18) |
| [scons](/t/the-scons-plugin/8629) | integrates projects that use the SCons construction tool | core22</br>core18 |
| [waf](/t/the-waf-plugin/8630) | integrate projects using the Waf build automation tool | core18

## Platforms

### Linux kernel

| Plugin name |  Description | Base support |
|--|--|--|
| [kbuild](/t/the-kbuild-plugin/8633) | build parts that use the Linux kernel build system (kBuild) | core18 |
| [kernel](/t/the-kernel-plugin/8642) | derived from the *kbuild* plugin and used to build your own kernel | core18 |

### Robot Operating System (ROS)

| Plugin name |  Description | Base support |
|--|--|--|
| [ament](/t/the-ament-plugin/8643) | uses ament_cmake to build parts for version 2 of the Robot Operating System (ROS 2) | core18 |
| [catkin](/t/the-catkin-plugin/8644) | build catkin-based parts, typically used with version 1 of the Robot Operating System (ROS 1) | [core20](/t/the-catkin-plugin/8644#heading--core20) <br /> [core18](/t/the-catkin-plugin/8644#heading--core18) |
| [catkin-tools](/t/the-catkin-tools-plugin/8645) | alternative method for building projects using version 1 of the Robot Operating System (ROS 1)   | [core20](/t/the-catkin-tools-plugin/8645#heading--core20) <br /> [core18](/t/the-catkin-tools-plugin/8645#heading--core18) |
| [colcon](/t/the-colcon-plugin/11895) | build colcon-based parts, typically used with version 2 of the Robot Operating System (ROS 2)  | [core22](/t/the-colcon-plugin/11895#heading--core22) <br />[core20](/t/the-colcon-plugin/11895#heading--core20) <br /> [core18](/t/the-colcon-plugin/11895#heading--core18) |

## Tools

| Plugin name |  Description | Base support |
|--|--|--|
| [dump](/t/the-dump-plugin/8007) | simply dumps the contents from the specified source | core22 <br /> core20 <br /> core18 |
| [nil](/t/the-nil-plugin/8646) | useful for parts with no source to import | core22 <br /> core20 <br /> core18 |
| [plainbox-provider](/t/the-plainbox-provider-plugin/8647) | create parts containing a Plainbox test collection known as a *provider*  | core18 |8