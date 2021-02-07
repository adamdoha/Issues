
#### spring boot 2.0의 profile은 기본적으로 다음 순서로 찾는다.


1. resources/config 디렉토리의 application.properties(혹은 application.yaml 파일)

2. resources 디렉토리의 application.properties(혹은 application.yaml 파일)

3. classpath/config 디렉토리의 application.properties(혹은 application.yaml 파일)

4. classpath 디렉토리의 application.properties(혹은 application.yaml 파일)


이제 같은 directory 내에서도 다음과 같은 우선순위로 경쟁을 한다.

1. application.properties(application.yaml)를 찾는다.

2. application.properties(application.yaml)에서 spring.profiles.active, spring.profiles.include가 설정돼있지 않다면 기본적으로 profile에 default가 setting 되고, 아래와 같은 로그를 볼 수 있다. `No active profile set, falling back to default profiles: default`

3. 설정된 profile에 따라서 application-{profile}.properties(application-{profile}.yaml)을 찾는다.
ex) spring.profiles.active=local, spring.profiles.include=core의 경우에는 application-local.properties(application-local.yaml), application-core.properties(application-core.yaml)
