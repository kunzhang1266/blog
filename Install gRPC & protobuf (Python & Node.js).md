# 安装 gRPC 与 protobuf

环境:

* 系统: Ubuntu Desktop 18.04.1 LTS
* 语言: Python & Node.js

---

## gRPC

> 如果使用的是 python3 则使用 `pip3`

```bash
# 安装 gRPC
pip install grpcio

# 安装 grpc 的 protobuf 工具
pip install grpcio-tools
```

## protobuf

### Python

```bash
# 安装 protobuf
pip install protobuf
```

### 下载并编译 protobuf 编译器

```bash
# 安装依赖库
sudo apt-get install autoconf automake libtool curl make g++ unzip

# 拉取源码
git clone https://github.com/protocolbuffers/protobuf.git
cd protobuf
git submodule update --init --recursive
./autogen.sh

# 构建并安装 protoc
./configure
make
make check
sudo make install
sudo ldconfig # 刷新共享库缓存
```

> 此步骤来自 [README.md](https://github.com/protocolbuffers/protobuf/tree/master/src)。

### 编译 proto 文件

```bash
python -m grpc_tools.protoc -I$SOURCE_DIR --python_out=$PYTHON_OUT_DIR --grpc_python_out=$GRPC_PYTHON_OUT_DIR $SOURCE_FILE
```

## Node.js

```bash
npm install grpc-tools --save-dev
npm install google-protobuf --save
npm install grpc --save
```

### 编译 proto 文件

```bash
./node_modules/grpc-tools/bin/protoc --js_out=import_style=commonjs,binary:$JS_OUT_DIR --plugin=protoc-gen-grpc=./node_modules/grpc-tools/bin/grpc_node_plugin --grpc_out=$GRPC_JS_OUT_DIR $SOUCE_FILE
```

## 注意

### 使用 Python3 运行时报错

报错内容：

```text
    import xxx_pb2 as xxx__pb2
ModuleNotFoundError: No module named 'xxx_pb2'
```

需要修改 `xxx_pb2_grpc.py` 中 `import xxx_pb2 as xxx__pb2` 为 `import xxx_pb2所在目录.xxx_pb2 as xxx__pb2`

> 参考 [python同目录下模块的导入问题](https://segmentfault.com/q/1010000013301780)。
