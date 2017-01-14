#Webpack-Devserver-Hmr-Start-Sample
> dev-server + HotModuleReplacementPlugin + ES6-Babel + S3 배포설정이 장착된 웹팩 기본 스타트 샘플입니다.

##설치
```
npm install
```

##개발시
```
npm run dev
```

##빌드
```
npm install build
```

##AWS S3 배포
아래와 같이 실행하되, 설정파일(webpack.config.deploy.js)의 s3 키값을 세팅해야합니다. 옵션관련 정보는 [s3-plugin-webpack](https://github.com/MikaAK/s3-plugin-webpack)를 참고하시길.
```
npm install deploy
```

##AWS CLI 배포 방법
웹펙을 통하지 않고 AWS CLI를 통해서도 S3에 배포할 수 있습니다.
1. [aws CLI](https://aws.amazon.com/ko/cli/)를 설치.
Mac Sierra 에서 awscli 가 정상적으로 설치가 되지 않는 경우, --ignore-installed six 옵션을 추가하여 설치합니다

```
sudo pip install awscli --ignore-installed six
```

2. cloudfront 캐시삭제를 위한 설정
```
aws configure set preview.cloudfront
```
access key와 secret access key를 요구하면 deploy.sh파일을 보고 복사해서 입력하십시요.
aws cli설정에 관한 자세한 설명은 [Configuring the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)를 참고하세요.

4. 배포 명령어
```
sh deploy-sample.sh
```
위 배포 명령어를 실행하기 전에 `deploy-sample.sh` 파일에 몇 가지 설정을 직접해야합니다. 아래 코드는 여러분이 수정해야할 부분만을 보여주고 있습니다. 중괄호{}안의 내용을 본인의 설정에 맞게 기입한 후 사용하십시요.
```
BUCKET={your aws bucket}
SOURCE_DIR={upload dir name}

export AWS_ACCESS_KEY_ID={your aws access key id}
export AWS_SECRET_ACCESS_KEY={your aws secret access key}
export AWS_DEFAULT_REGION={your aws default region}
```

##참고
- [webpack](http://webpack.github.io/)
- [AriaFallah의  WebpackTutorial](https://github.com/AriaFallah/WebpackTutorial/tree/master/part1) 중 [Example 6 - The Development Server](https://github.com/AriaFallah/WebpackTutorial/tree/master/part1/example)
- [webpack s3 deploy plugin](https://github.com/MikaAK/s3-plugin-webpack)
