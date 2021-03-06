# RxSocialLogin [![CircleCI](https://circleci.com/gh/WindSekirun/RxSocialLogin.svg?style=svg)](https://circleci.com/gh/WindSekirun/RxSocialLogin) [![](https://jitpack.io/v/WindSekirun/RxSocialLogin.svg)](https://jitpack.io/#WindSekirun/RxSocialLogin)

 [![](https://img.shields.io/badge/Android%20Arsenal-RxSocialLogin-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/7028) [![Awesome Kotlin Badge](https://kotlin.link/awesome-kotlin.svg)](https://github.com/KotlinBy/awesome-kotlin)


![](graphics/logo.png)

*The license information for logo is located at the bottom of the document.*

These instructions are available in their respective languages.

* [English](README.md) - Latest update: 2018-10-10, [@WindSekirun](https://github.com/windsekirun)
* [한국어](README-ko.md) - Latest update: 2018-10-10, [@WindSekirun](https://github.com/windsekirun)
* [日本語](README-jp.md) - Latest update: 2018-10-10, [@WindSekirun](https://github.com/windsekirun)

## 소개

본 안드로이드 라이브러리는 15개의 플랫폼에 대해 소셜 로그인을 제공하는 라이브러리로, [RxJava2](https://github.com/ReactiveX/RxJava) 와 [Kotlin](http://kotlinlang.org/), 그리고 [Firebase 인증](https://firebase.google.com/docs/auth/) 의 도움으로 제공됩니다.

이 라이브러리는 제작자인 [@WindSekirun](https://github.com/windsekirun) 의 [SocialLogin](https://github.com/WindSekirun/SocialLogin) 라는 라이브러리의 개선 버전이며, 아래와 같은 차이점을 가지고 있습니다.

* 결과 전달 방식이 Listener 가 아닌 RxJava 로 통해 전달되는 것으로 변경되었습니다.
* 원본이 Java 로 작성된 것에 비해, 개선 버전은 Kotlin 으로만 작성되었습니다.
* 원본이 6개의 플랫폼을 지원했던 반면, 개선판은 15개의 플랫폼을 제공합니다.
* Kotlin으로 작성된 *Type-Safe builder* 를 제공합니다.
* 모든 메서드와 코드를 재작성 하였습니다.
* Kotlin 으로 작성되었지만 Java 와 호환되도록 고려되었습니다.

## 지원되는 플랫폼

| 플랫폼                                                       | 데이터                                                       | 버전  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ----- |
| [Disqus](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Disqus) | id, name, email, nickname, profilePicture                    | 1.0.0 |
| [Facebook](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Facebook) | id, name, email, profilePicture, gender, firstName           | 0.5.0 |
| [Foursquare](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Foursquare) | id, name, email, firstName, gender, birthDay, profilePicture | 1.0.0 |
| [Github](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Github) | id, name, email, profilePicture, emailVerified               | 1.0.0 |
| [Google](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Google) | id, name, email, profilePicture, emailVerified               | 0.5.0 |
| [Kakao](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Kakao) | id, name, email, profilePicture, thumbnailImage, ageRange, birthDay, gender, emailVerified | 0.5.0 |
| [Line](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Line) | id, name, accessToken                                        | 0.5.0 |
| [LinkedIn](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-LinkedIn) | id, name, email, profilePicture, firstName                   | 1.0.0 |
| [Naver](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Naver) | id, name, email, nickname, gender, profilePicture, age, birthDay | 0.5.0 |
| [Twitch](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Twitch) | id, name, email,  profilePicture                             | 1.0.0 |
| [Twitter](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Twitter) | id, name, nickname, email, profilePicture                    | 0.5.0 |
| [VK](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-VK) | id, name, email, profilePicture, nickname, firstName, birthDay | 1.0.0 |
| [Windows](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Windows) | id, name, email                                              | 1.0.0 |
| [Wordpress](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Wordpress) | id, name, email, profilePicture, emailVerified               | 1.0.0 |
| [Yahoo](https://github.com/WindSekirun/RxSocialLogin/wiki/Guide-to-Yahoo) | id, name                                                     | 1.0.0 |

각 플랫폼의 이름을 누르면 해당 플랫폼의 적용 방법 가이드로 이동합니다.

## 불러오기

루트 폴더의 `build.gradle` 에 아래 주소를 추가합니다.

```groovy
allprojects {
	repositories {
		maven { url 'http://devrepo.kakao.com:8088/nexus/content/groups/public/' }
		maven { url 'https://jitpack.io' }
	}
}
```

사용할 모듈의 `build.gradle` 에 아래의 의존성을 추가합니다.

```groovy
dependencies {
	implementation 'com.github.WindSekirun:RxSocialLogin:1.1.0'
    
	// RxJava
	implementation 'io.reactivex.rxjava2:rxandroid:lastest-version'
	implementation 'io.reactivex.rxjava2:rxjava:lastest-version'
}
```

RxJava는 활동이 활발한 라이브러리로, 새로운 개선 사항을 적용하려면 항상 최신 버전을 유지해야 합니다. 따라서 RxJava 를 의존성의 맨 아래에 추가하는 것을 권장합니다.

* RxAndroid: <a href='http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22io.reactivex.rxjava2%22%20a%3A%22rxandroid%22'><img src='http://img.shields.io/maven-central/v/io.reactivex.rxjava2/rxandroid.svg'></a>

* RxJava: <a href='http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22io.reactivex.rxjava2%22%20a%3A%22rxjava%22'><img src='http://img.shields.io/maven-central/v/io.reactivex.rxjava2/rxjava.svg'></a>

#### 1.0.0에서의 마이그레이션

1.1.0은 1.0.0에 비해 숙지해야 될 큰 변화가 있습니다. 다음은 그 변화점입니다.

- 자바 빌더로부터 DSL 빌더로의 마이그레이션
- RxSocialLogin의 인스턴스 관리
- onActivityResult 이벤트 공통화
- 결과 구독 방법 변경

[Release Notes 는 여기에서 볼 수 있습니다.](https://github.com/WindSekirun/RxSocialLogin/pull/26)

## 아주 쉬운 5단계 사용법

먼저, `Application` 클래스에서 `ConfigDSLBuilder`를 사용하여 모듈을 초기화합니다. `ConfigDSLBuilder` 는 각 플랫폼에 맞는 설정을 구성할 수 있도록 제공됩니다.

```kotlin
class MainApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        initSocialLogin {
            facebook(getString(R.string.facebook_api_key)) {
                behaviorOnCancel = true
                requireWritePermissions = false
                imageEnum = FacebookConfig.FacebookImageEnum.Large
            }
        }
    }
}

```

`initSocialLogin` 블록 내에서 facebook, google와 같은 **플랫폼 이름을 가진 메서드를 사용할 수 있습니다.** `setup` 파라미터를 제외한 나머지 파라미터는 소셜 로그인 기능을 사용하기 위해 반드시 필요한 정보입니다.

`setup` 파라미터는 생성된 Config 객체(예, FacebookConfig) 를 제공하고, `behaviorOnCancel`, `imageEnum` 등의 추가적인 옵션을 제공하는 함수입니다. 메서드에 제공되지 않을 수 있으나 null로 제공할 수는 없습니다.

비록 `ConfigDSLBuilder` 가 *Kotlin Type-Safe builders* 로 구성되었어도, **여전히 자바 언어와 호환됩니다.** 원래의 `setup` 고차함수가 제공하는 기능을 `ConfigFunction` 이라는 인터페이스로 제공합니다.

[Kotlin](https://github.com/WindSekirun/RxSocialLogin/blob/1.1-dev/demo/src/main/java/com/github/windsekirun/rxsociallogin/test/MainApplication.kt) 와 [Java](https://github.com/WindSekirun/RxSocialLogin/blob/1.1-dev/demo/src/main/java/com/github/windsekirun/rxsociallogin/test/JavaApplication.java) 로 된 `ConfigDSLBuilder` 의 전체 예제를 볼 수 있습니다.

다음으로, `Activity` 의 `onStart` 메서드에서 `RxSocialLogin.initialize(this)` 를 호출합니다.

```kotlin
override fun onStart() {
    super.onStart()
    RxSocialLogin.initialize(this)
}
```

1.1.0부터 `RxSocialLogin` 클래스가 로그인 객체의 인스턴스를 관리하므로 각 로그인 객체의 초기화를 신경쓸 필요는 없습니다.

다음으로, `onActivityResult` 메서드에서 ``RxSocialLogin.activityResult(requestCode, resultCode, data)`` 를 호출합니다.

```kotlin
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent ? ) {
    super.onActivityResult(requestCode, resultCode, data)
    RxSocialLogin.activityResult(requestCode, resultCode, data)
}
```

다음으로, 결과를 얻고자 하는 곳에 ``RxSocialLogin.result`를 호출합니다. 액티비티 외 클래스에도 사용이 가능합니다.

```kotlin
RxSocialLogin.result()
    .subscribe({ item -> 

    }, { throwable ->

    }).addTo(compositeDisposable)
```

마지막으로, `RxSocialLogin.login(PlatformType.FACEBOOK)` 를 호출하여 소셜로그인 기능을 시작합니다.

### 사용시의 안내사항

#### 프로가드(Proguard) 적용

[샘플 앱의 프로가드 규칙](https://github.com/WindSekirun/RxSocialLogin/blob/master/demo/proguard-rules.pro) 을 참고하여 적용하기 바랍니다.

#### 제약 - 모든 행동은 메인 스레드를 유지해야 함

모든 행동은 메인 스레드 내에서 작동되야 합니다. 라이브러리 내부에서 네트워크를 사용할 경우에는 내부에서 [Fuel](https://github.com/kittinunf/Fuel) 를 사용하여 올바르게 처리되니, `RxSocialLogin` 으로 반환된 `Observable` 는 메인 스레드를 유지해야 합니다. 만일 메인 스레드가 아닐 경우 바로 로그인 실패가 이루어집니다.

즉, 아래의 경우에는 처리되지 않고 바로 `LoginFailedException` 으로 처리됩니다.

```kotlin
RxSocialLogin.result()
		.subscribeOn(Schedulers.io())
		.observeOn(AndroidSchedulers.mainThread())
		...
```

이 주의점으로 인해 **네트워크 처리 후 `flatMap` 등으로 바로 소셜 로그인을 시작하는 것이 허용되지 않습니다.** 이러한 케이스를 처리해야 될 경우에는 네트워크 처리 후 subscribe 내에서 따로 `RxSocialLogin` 를 호출하는 것이 바람직합니다.

#### OnErrorNotImplementedException가 발생

공통적인 오류로 [OnErrorNotImplementedException](http://reactivex.io/RxJava/javadoc/io/reactivex/exceptions/OnErrorNotImplementedException.html) 가 발생할 경우가 있는데, 이는 `subscribe` 당시 `onError` 에 대해 처리하지 않았기 때문입니다. 

#### UndeliverableException가 발생

0.5.0 기준으로 [UndeliverableException](http://reactivex.io/RxJava/javadoc/io/reactivex/exceptions/UndeliverableException.html) 가 발생할 경우가 있는데, 이는 Exception 이 `onError` 으로 전달되지 못하였을 때 발생하는 문제입니다. `RxJavaPlugins.setErrorHandler { e -> }` 라는 문구로 해결이 가능하나, 이는 RxJavaPlugins 의 전체 행동을 변경하므로 주의하시기 바랍니다. 

1.0.0 이상에서는 이 문제가 발생하지 않도록 `LoginFailedException` 가 `IllegalStateException` 를 상속하도록 변경되었습니다. 따라서 최신 버전에서는 발생하지 않도록 의도되었습니다.

이에 대한 자세한 사항은 [Error handling](https://github.com/ReactiveX/RxJava/wiki/What's-different-in-2.0#error-handling) 문서를 참조하시기 바랍니다.

#### API 21 미만 지원

현재(1.1.0), **minSdkVersion 으로 API 16을 지원하고 있으나**, ``com.microsoft.identify.client:msal`` 라이브러리가 minSdkVersion 으로 API 26을 지원하고 있습니다.

[issue #263 of AzureAD/microsoft-authentication-library-for-android](https://github.com/AzureAD/microsoft-authentication-library-for-android/issues/263) 에 따르면, 해당 라이브러리를 오버라이드 하는 것으로 minSdkVersion에 대한 충돌을 회피할 수 있습니다.

충돌을 해결하기 위하여, 아래 코드를 AndroidManifest.xml에 삽입합니다.

```xml
<uses-sdk tools:overrideLibrary="com.microsoft.identity.msal"/>
```

## 제작자 & 기여자

* 제작자: [@WindSekirun](https://github.com/windsekirun), 메일 [pyxis@uzuki.live](mailto:pyxis@uzuki.live)
* 기여자: [Contributors](https://github.com/WindSekirun/RxSocialLogin/graphs/contributors)

버그 발견 사항, 개선 사항, 새로운 플랫폼 추가 등 다양한 사항을 [이슈 트래커](https://github.com/WindSekirun/RxSocialLogin/issues) 에서 접수받고 있습니다. [Pull Requests](https://github.com/WindSekirun/RxSocialLogin/pulls) 도 언제나 환영입니다.

## 라이센스

* ReactiveX 로고는 [Seeklogo](https://seeklogo.com/vector-logo/284342/reactivex) 에서 가져왔습니다. 
* 로고에 사용된 폰트는 Hanken Design Co. 의 [Hanken round](https://www.behance.net/gallery/18871499/Hanken-Round-Free-Typeface) 이며 본 폰트는 SIL OFL를 따릅니다. 프로젝트 내에 로고에 대한 PSD 파일이 있습니다.
* 샘플에 사용된 플랫폼 로고에 대한 저작권은 각 회사에 존재합니다. RxSocialLogin 라이브러리는 플랫폼 회사와 연관이 없습니다.

```
Copyright 2017 - 2018 WindSekirun (DongGil, Seo)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

