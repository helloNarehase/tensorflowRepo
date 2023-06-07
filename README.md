Tensorflow 보고서
=====
컴퓨터를 초기화 했거나 하는 등의 이유로 Tensorflow를 재설치 한다면 `GPU 학습이 안되는 현상이 발생 할것이다.`

그러한 이유는 Tensorflow를 최신 릴리즈 노트를 보면 알게 되는데
> tensorflow 2.10.x 이후 버전 부터는 windows에서 GPU학습을 지원하지 않습니다.

뜻밖에 사건이다. 이에 tensorflwo를 2.10.0으로 다운그레이드가 안되는 문제점이 있다. 그러나 이는 정말 쉬운 문제이다.
>Version issue!

텐서플로우는 상위 호환이 안되는 문제가 있기에 `tensorflow 2.10.x`는 `python 3.10.x`를 사용해야 한다. 

3일 걸친 밤을 지세운 눈물겨운 똥꼬쇼의 결과 이다.

결과 ->
> Q. Version error when downgrading TensorFlow.<br>

A. Check the version compatibility of Python and TensorFlow.
```
TensorFlow 2.10.x requires Python 3.10.x.
Note the version.
```

# + cuDnn -> Zlib err
cuDnn까지 설정을 맞추었음에도 GPU를 사용하지 못하거나 에러가뜰수 있다. 이럴때에는 파일 하나만 넣어주자.

다운받기에는 힘이드니 아래에 공유링크를 작성한다.
``` 
https://drive.google.com/drive/folders/1mOwSc-M_Vz_ZCeXYlKHx5PHjBC0wPHeh?usp=drive_link 
```
아래파일을 다운 받았으면 
```
C:\\program\\cuda\\cuda11.8\\bin
```
위 디렉토리에 `zlibwapi.dll`을 넣어 주면 된다.<br>
이래도 안된다면 
``` py
with tf.device(".\\GPU:0"):
    ... 학습 코드를 넣으시오.
```






----
작성 시작일 - 06.07
