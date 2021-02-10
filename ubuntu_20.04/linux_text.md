- モジュール
  - カーネル内のファイルをモジュールファイツという形で分離・格納しておき、必要に応じて稼働中のカーネルに組み込んだり、切り離したりできる仕組み


# Linuc kernelのビルドの仕方


```
sudo apt update
sudo apt install build-essential bc bison flex libelf-dev libssl-dev libncurses5-dev
```

```
# https://www.kernel.org/
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.4.96.tar.xz
tar xvf https://www.kernel.org/
```



```
# もともとあるコンフィグを利用
cp /boot/config-5.4.0-58-generic  .config

# .configとこれからビルドするカーネルの設定変数の違いを吸収するコマンド
make syncconfig
```

```
# カーネルのビルド
#  CPU数で並列実行
make -j `nproc`
# インストール
sudo make modules_install
sudo make install
```