### Gradle 이란?
- Java에서 라이브러리 의존성을 관리해주는 빌드 도구이다.
- 그루비(Grrovy, ex. def a = 20)를 기반으로 한 빌드 도구이다.

### plugin
- 캡슐화된 빌드로직으로 빌드스크립트에서 사용자가 직접 정의해서 사용할수도 있고
이미 만들어진 plugin을 불러와서 사용할수도 있다.


## Sample Code
```groovy
plugins {
    id 'java'
}

group 'org.example'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.7.0'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.7.0'

}

test {
    useJUnitPlatform()
}
```

### plugins
- 번들링, 테스트 등을 진행할 때 여러 기능을 제공하기 위한 플로그인을 설정하는 공간이다.
- 위 Sample Code를 보면 java 플러그인을 사용하겠다는 의미로, 해당 플러그인은 자바 코드를 컴파일하고, 테스트를
실행할 수 있게 해준다.

### dependencies
- 프로젝트가 의존하는 외부 라이브러리를 기술하는 공간이다.
- 의존성을 컴파일시에만 포함시킬 것인지 런타임시에도 포함시킬 것인지 정해야 한다.
  - lombok 같은 것들은 컴파일시에만 필요한 대표적인 의존석이다.
- 컴파일 시에 해당 의존성을 포함하지 않도록 하면 컴파일 시간을 줄일 수 있다.
  - compieleOnly : 해당 의존성을 컴파일시에만 포함
  - runtimeOnly : 해당 의존성을 런타임시에만 포함
- 컴파일시, 런타임시 상관없이 모든 과정에 의존성을 추가하는 것은 두가지 지시어가 있다.
  (참조하고 있는 다른 의존성의 재빌드 범위차이)
  - compile : 해당 의존성을 직/간접적으로 의존하고 있는 모든 의존성을 재빌드한다.
  - implementation : 해당 의존성을 직접 의존하고 있는 의존성만 재빌드한다.
- annotationProcessor
  - lombok을 사용할 때 필수로 추가되어야 하는 지시어로 이를 포함하지 않으면
컴파일러는 lombok에서 제공하는 어노테이션을 인식하지 못한다.
  - 컴파일러에게 어노테이션을 확인할 때 lombok도 봐달라고 요청하는 것이다. Gradle에서는 컴파일
classPath와 어노테이션 프로세서 classPath를 분리하여 빌드 성능을 향상시키는데 기본적으로 포함되어 있는
어노테이션이 아니라면 annotationPrecessor를 통해 명시적으로 추가해줘야 한다.

### repositories
- 여러 라이브러리를 가지고 있는 저장소이다.
- 주로 사용되는 저장소는 mavenCentral, jcenter, google 등이 있다.

### test
- Junit 또는 TestNG 테스트를 실행시킨다.

### others
- group, version은 해당 프로젝트의 여러 기능을 기술함






