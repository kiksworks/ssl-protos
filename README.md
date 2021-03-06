# ssl-protos ![](https://github.com/kiksworks/ssl-protos/workflows/Build/badge.svg)

RoboCup SSLでよく使う `*.proto` ファイル ([ssl-vision][], [ssl-refbox][], [ssl-game-controller][], [grSim][]) の詰め合わせ.

## Requirements

- CMake 3.10+
- Protocol Buffers 2.6+

## Usage

### CMakeを使っている場合

このリポジトリを `git submodule` 等を使ってプロジェクトの任意のディレクトリにcloneします.

```
$ git submodule add https://github.com/kiksworks/ssl-protos.git ssl-protos
```

プロジェクトの `CMakeLists.txt` に以下のように記述し, 必要な実行ファイルに `ssl-protos` をリンクしてください.

```cmake
add_subdirectory(ssl-protos)

add_executable(main main.cc)
target_link_libraries(main ssl-protos)
```

## Note

本家の `*.proto` ファイルから, いくつかの変更を加えています.

- package名 (`ssl_protos.xxx`) をセット
- いくつかのmessage名, ファイル名を変更

詳細はコードを確認してください.

## Author

Kenta Sato (<https://github.com/Tosainu>)

## License

The project is licensed under [GNU LGPLv3 or later](LICENSE).

- `./grsim/*.proto`
  - [GPLv3 or later](https://github.com/mani-monaj/grSim/blob/master/LICENSE.md)
- `./refbox/*.proto`
  - [GPLv3 or later](https://github.com/RoboCup-SSL/ssl-game-controller/blob/master/LICENSE)
- `./vision/*.proto`
  - [GPLv3](https://github.com/RoboCup-SSL/ssl-vision/blob/master/COPYING)

[ssl-vision]: https://github.com/RoboCup-SSL/ssl-vision
[ssl-refbox]: https://github.com/RoboCup-SSL/ssl-refbox
[grSim]:      https://github.com/mani-monaj/grSim
[ssl-game-controller]: https://github.com/RoboCup-SSL/ssl-game-controller
