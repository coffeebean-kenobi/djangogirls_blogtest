# Django Girlsを通じてDjangoを学習する


## 環境
mac OS X
~/djangogirls
python3.7.3
docker

## 参考

### Django Girlsサイト
https://tutorial.djangogirls.org/ja/


### pyenv使い方
pyenv-vertualenvや仮想環境の作り方など
https://qiita.com/ysdyt/items/5008e607343b940b3480

予めpyenvにインストールされているバージョン出ないと仮想環境はできなさそう


### bash->zsh読みかえ
zsh tips
https://qiita.com/muran001/items/7b104d33f5ea3f75353f

pyenv virtualenv 3.6.5 test

### anaconda仮想環境
https://qiita.com/ozaki_physics/items/985188feb92570e5b82d

## 実行コマンド
pyenvでやってみた
```
% pyenv install 3.7.3
% pyenv virtualenv 3.7.3 myenv 
% pyenv local 3.7.3
% % pip --version
pip 19.0.3 from /Users/tasakataishi/.pyenv/versions/3.7.3/lib/python3.7/site-packages/pip (python 3.7)
```
[version]で使ってたものを使いたければ、--system-site-packageというオプションをつける。
```
% pyenv activate myenv  
->動かない
% pyenv deactivate myenv
% pyenv uninstall myenv 
```

やっぱりanacondaで環境を作成
 anacondaを有効化

```
~% pyenv global anaconda3-2020.02

% conda create -n djangogirls python=3.7
(もしくはGUIから)
以下のパッケージと一緒にダウンロードされる
  ca-certificates    pkgs/main/osx-64::ca-certificates-2020.6.24-0
  certifi            pkgs/main/osx-64::certifi-2020.6.20-py37_0
  libcxx             pkgs/main/osx-64::libcxx-10.0.0-1
  libedit            pkgs/main/osx-64::libedit-3.1.20191231-h1de35cc_1
  libffi             pkgs/main/osx-64::libffi-3.3-hb1e8313_2
  ncurses            pkgs/main/osx-64::ncurses-6.2-h0a44026_1
  openssl            pkgs/main/osx-64::openssl-1.1.1g-h1de35cc_0
  pip                pkgs/main/osx-64::pip-20.2.2-py37_0
  python             pkgs/main/osx-64::python-3.7.7-hf48f09d_4
  readline           pkgs/main/osx-64::readline-8.0-h1de35cc_0
  setuptools         pkgs/main/osx-64::setuptools-49.2.0-py37_0
  sqlite             pkgs/main/osx-64::sqlite-3.32.3-hffcf06c_0
  tk                 pkgs/main/osx-64::tk-8.6.10-hb0a8c7a_0
  wheel              pkgs/main/osx-64::wheel-0.34.2-py37_0
  xz                 pkgs/main/osx-64::xz-5.2.5-h1de35cc_0
  zlib               pkgs/main/osx-64::zlib-1.2.11-h1de35cc_3


% conda activate myenv

```
プロンプトが変わる（やはり仮想環境はanacondaが優先されるようになっている）
```
(myenv) tasakataishi@ttimaac djangogirls % 
```



```
source deactivate
conda remove -n myenv --all
```

GUIからdjangogirlsの仮想環境を作成
djangoをインストール
```
% conda install django
```
 
 
 プロジェクト作成
```
% django-admin startproject mysite .
```
ブログアプリ作成
 
```
 % python manage.py startapp blog
```

models.py変更後

```
# 
python manage.py makemigrations blog
python manage.py migrate blog 
```
管理ユーザー作成

* Username: ola
* Email address: ola@example.com
* Password:olah

```
python manage.py createsuperuser
```
http://127.0.0.1:8000/admin/
で確認、ブログ記事とユーザ作ってみる

* ユーザ名：tai
* pass:7uhad8999
->パスワードポリシーの変更などどこで？


gitにあげる
```
git init
git commit -m "first commit"
git remote add origin https://github.com/coffeebean-kenobi/djangogirls_blogtest.git
git push -u origin master
```
 pythonanywhere側での設定
APIトークン作成
8f1a9e516013a6de11535506528ebb157c8f04fe
bashに入る
```
$ pip3.7 install --user pythonanywhere
$ pa_autoconfigure_django.py --python=3.7 https://github.com/coffeebean-kenobi/djangogirls_blogtest.git
(なぜかうまくいかなかったので--nukeをつけて再度実行)
```
ユーザ作成
```
$ python manage.py createsuperuser
ローカルと同じ
```


