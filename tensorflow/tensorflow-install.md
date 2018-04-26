# 텐서플로우 설치하기

## 설치하기
macOS High Sierra버전에서 pip를 통해 턴서플로우를 설치하는 법

pip 설치
```
sudo easy_install pip
sudo easy_install --upgrade six
```

텐서플로우 설치
```
sudo -H pip install tensorflow
```

## 에러

```
Cannot uninstall 'numpy'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.
```
라는 오류로 설치가 되지않았는데,

아래 코드로 설치하니 설치가 됬다.
```
sudo pip install --ignore-installed numpy
```
## 레퍼런스
- [https://www.tensorflow.org/install/install_mac#common_installation_problems](https://www.tensorflow.org/install/install_mac#common_installation_problems)
- [https://github.com/tensorflow/tensorflow/issues/6331](https://github.com/tensorflow/tensorflow/issues/6331)
- [https://tensorflowkorea.gitbooks.io/tensorflow-kr/content/g3doc/get_started/os_setup.html](https://tensorflowkorea.gitbooks.io/tensorflow-kr/content/g3doc/get_started/os_setup.html)