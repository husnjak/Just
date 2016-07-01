[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![CocoaPods](https://img.shields.io/cocoapods/v/Just.svg)](https://cocoapods.org/pods/Just)
[![Build Status](https://travis-ci.org/JustHTTP/Just.svg?branch=swift-2.0)](https://travis-ci.org/JustHTTP/Just)
![MIT License](https://img.shields.io/cocoapods/l/Just.svg)
![Supported Flatform](https://img.shields.io/cocoapods/p/Just.svg)

<img src="https://raw.githubusercontent.com/JustHTTP/Just/master/Docs/IconMasked.png" width="280" height="280">

Just is a client-side HTTP library inspired by [python-requests][] - HTTP for Humans.

Just supports Swift 3. You can use it with Swift 2 with version
[0.4.7](https://github.com/JustHTTP/Just/tree/v0.4.7).

*Follow [@JustHTTP][twitter] for updates, if you are into that kind of things* 😉

[python-requests]: http://python-requests.org "python-requests"
[twitter]: https://twitter.com/JustHTTP

#   Features

Just lets you to the following effortlessly:

-   URL queries
-   custom headers
-   form (`x-www-form-encoded`) / JSON HTTP body
-   redirect control
-   multipart file upload along with form values.
-   basic/digest authentication
-   cookies
-   timeouts
-   synchronous / asynchronous requests
-   upload / download progress tracking for asynchronous requests
-   link headers
-   friendly accessible results

#  Use

The simplest request with Just looks like this:

```swift
//  A simple get request
Just.get("http://httpbin.org/get")
```

The next example shows how to upload a file along with some data:

```swift
//  talk to registration end point
let r = Just.post(
    "http://justiceleauge.org/member/register",
    data: ["username": "barryallen", "password":"ReverseF1ashSucks"],
    files: ["profile_photo": .URL(fileURLWithPath:"flash.jpeg", nil)]
)

if r.ok { /* success! */ }
```

Here's the same example done asynchronously:

```swift
//  talk to registration end point
Just.post(
    "http://justiceleauge.org/member/register",
    data: ["username": "barryallen", "password":"ReverseF1ashSucks"],
    files: ["profile_photo": .URL(fileURLWithPath:"flash.jpeg", nil)]
) { r in
    if r.ok { /* success! */ }
}

```

Read *Getting Started* [on the web][starting link] or
[in this playground][starting playground] to learn more!

[starting playground]: https://github.com/JustHTTP/Just/raw/master/Docs/QuickStart.zip
[starting link]: http://docs.justhttp.net/QuickStart.html

#  Install

Here are some ways to leverage Just.

## Carthage (recommended)

Include the following in your Cartfile:

    github "JustHTTP/Just"

Just includes dynamic framework targets for both iOS and OS X.

## CocoaPods

The usual way:

    platform :ios, '8.0'
    use_frameworks!

    target 'MyApp' do
      pod 'Just'
    end

## Manual

Drop `Just.xcodeproj` into your project navigator. Under the *General* tab of
your project settings, use the plus sign to add `Just.framework` to
*Linked Framework and Libraries*. Make sure to include the correct version
for your target's platform.

It's also common to add Just as a git submodule to your projects repository:

    cd path/to/your/project
    git submodule add https://github.org/JustHTTP/Just.git


## Source File

Put `Just.swift` directly into your project. Alternately, put it in the
*Sources* folder of a playground. (The latter makes a fun way to explore the
web.)


[Carthage]: https://github.com/Carthage/Carthage "Carthage"


#  Contribute

Pull requests are welcome. Here are some tips for code contributors:

Work in `Just.xcworkspace`.

The tests for link headers relies on Github APIs, which has a low per-hour
limit. To overcome this, you can edit the Xcode build schemes and add
[environment variables][XcodeEnvVar] `GITHUB_USERNAME` and `GITHUB_TOKEN`.
Learn more about personal tokens [here][GithubToken].

For Xcode rebels, checkout `Makefile` (you'll need [xcpretty][]).

HTML documentation pages are generated by literate programmin tool [docco][]

[xcpretty]: https://github.com/supermarin/xcpretty "xcpretty"
[docco]: http://jashkenas.github.io/docco/ "docco"
[GithubToken]: https://developer.github.com/v3/#increasing-the-unauthenticated-rate-limit-for-oauth-applications 
[XcodeEnvVar]: http://nshipster.com/launch-arguments-and-environment-variables/

#  License

MIT, see [LICENSE.md](https://github.com/JustHTTP/Just/blob/master/LICENSE.md).
