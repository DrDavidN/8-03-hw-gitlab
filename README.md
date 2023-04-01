# 8-03-hw-gitlab
# 8.3. GitLab - Дрибноход Давид

## Задание 1.
![Скриншот настроек 1](https://github.com/DrDavidN/8-03-hw-gitlab/blob/main/z1img/runner_config.JPG) 
![Скриншот настроек1](https://github.com/DrDavidN/8-03-hw-gitlab/blob/main/z1img/runner_in_project.JPG)

## Задание 2.
```yaml

stages:
  - test
  - build

test:
  stage: test
  image: golang:1.17
  script:
   - go test .

build:
  stage: build
  image: docker:latest
  script:
   - docker build .

```
![Скриншот настроек1](https://github.com/DrDavidN/8-03-hw-gitlab/blob/main/z2img/build_result.JPG)
![Скриншот настроек1](https://github.com/DrDavidN/8-03-hw-gitlab/blob/main/z2img/build_result2.JPG)

## Задание 3.
```yaml

stages:
  - build
  - test

test:
  stage: test
  image: golang:1.17
  script: 
   - go test .
  rules:
    - changes:
        paths:
          - "*.go"

build:
  stage: build
  image: docker:latest
  script:
   - docker build .

```
