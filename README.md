timehack6435126
===

[![Maven Central](https://img.shields.io/maven-central/v/com.io7m.timehack6435126/com.io7m.timehack6435126.svg?style=flat-square)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.io7m.timehack6435126%22)
[![Maven Central (snapshot)](https://img.shields.io/nexus/s/com.io7m.timehack6435126/com.io7m.timehack6435126?server=https%3A%2F%2Fs01.oss.sonatype.org&style=flat-square)](https://s01.oss.sonatype.org/content/repositories/snapshots/com/io7m/timehack6435126/)
[![Codecov](https://img.shields.io/codecov/c/github/io7m-com/timehack6435126.svg?style=flat-square)](https://codecov.io/gh/io7m-com/timehack6435126)
![Java Version](https://img.shields.io/badge/21-java?label=java&color=e6c35c)

![com.io7m.timehack6435126](./src/site/resources/timehack6435126.jpg?raw=true)

| JVM | Platform | Status |
|-----|----------|--------|
| OpenJDK (Temurin) Current | Linux | [![Build (OpenJDK (Temurin) Current, Linux)](https://img.shields.io/github/actions/workflow/status/io7m-com/timehack6435126/main.linux.temurin.current.yml)](https://www.github.com/io7m-com/timehack6435126/actions?query=workflow%3Amain.linux.temurin.current)|
| OpenJDK (Temurin) LTS | Linux | [![Build (OpenJDK (Temurin) LTS, Linux)](https://img.shields.io/github/actions/workflow/status/io7m-com/timehack6435126/main.linux.temurin.lts.yml)](https://www.github.com/io7m-com/timehack6435126/actions?query=workflow%3Amain.linux.temurin.lts)|
| OpenJDK (Temurin) Current | Windows | [![Build (OpenJDK (Temurin) Current, Windows)](https://img.shields.io/github/actions/workflow/status/io7m-com/timehack6435126/main.windows.temurin.current.yml)](https://www.github.com/io7m-com/timehack6435126/actions?query=workflow%3Amain.windows.temurin.current)|
| OpenJDK (Temurin) LTS | Windows | [![Build (OpenJDK (Temurin) LTS, Windows)](https://img.shields.io/github/actions/workflow/status/io7m-com/timehack6435126/main.windows.temurin.lts.yml)](https://www.github.com/io7m-com/timehack6435126/actions?query=workflow%3Amain.windows.temurin.lts)|

## timehack6435126

A high-resolutiom timer JVM bug workaround.

## Features

* Enables high-resolution timers in the JVM.
* [OSGi-ready](https://www.osgi.org/)
* [JPMS-ready](https://en.wikipedia.org/wiki/Java_Platform_Module_System)
* ISC license.

## Motivation

The `com.io7m.timehack6435126` package implements the workaround for the
comedy of errors described by `JDK-6435126`.

1. Oracle introduce a JVM option ForceTimeHighResolution intended to force
   Windows based operating systems into using a high resolution timer instead
   of the usual low precision one.
2. Due to a mistake in the implementation, the ForceTimeHighResolution option
   actually ends up forcing the OS not to use the high resolution timer.
3. Years pass, and someone files a bug on the broken behaviour.
4. An anonymous developer at the company states that the behaviour has been
   broken for years, nobody has complained, and reasons that this means that
   users that are specifically asking for high resolution timers are satisfied
   with instead receiving low resolution timers.
5. Someone suggests a workaround that can be used at run-time to enable the
   high resolution timer.
6. Years pass.
7. An anonymous developer at the company states that the behaviour has been
   broken for so long, that there's no reason to fix it now.
8. The bug is rejected as "WONTFIX".

## Usage

Call `TimeHack6435126.enableHighResolutionTimer()` in your program's main
function prior to doing anything else.

All timer-related functions in the JVM will be significantly more precise
from that point onwards.

