# ssl-protos

RoboCup SSLでよく使う `*.proto` ファイル ([ssl-vision][], [ssl-refbox][], [grSim][]) の詰め合わせ.

## Requirements

* CMake 2.8.8+
- Protocol Buffers 2.6+

## Usage

### CMakeを使っている場合

このリポジトリを `git submodule` 等を使ってプロジェクトの任意のディレクトリにcloneします.

```
$ git submodule add https://github.com/kiksworks/ssl-protos.git ssl-protos
```

プロジェクトの `CMakeLists.txt` に以下のように記述し, 必要な実行ファイルに `ssl-protos` をリンクしてください.

```cmake
find_package(Protobuf REQUIRED)

add_subdirectory(ssl-protos)

add_executable(main main.cc)
add_dependencies(main ssl-protos)
target_link_libraries(main ssl-protos ${Protobuf_LIBRARY})
```

## Note

本家の `*.proto` ファイルから, いくつかの変更を加えています.

- package名 (`ssl_protos.xxx`) をセット
- いくつかのmessage名, ファイル名を変更

詳細はコードを確認してください.

## Author

Kenta Sato (<https://github.com/Tosainu>)

[ssl-vision]: https://github.com/RoboCup-SSL/ssl-vision
[ssl-refbox]: https://github.com/RoboCup-SSL/ssl-refbox
[grSim]:      https://github.com/mani-monaj/grSim
