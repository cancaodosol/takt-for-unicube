# ECCUBEプラグイン開発におけるルール（in Uni-Cube）

## 前提

このプロジェクトでは、UniCubeというECCUBEのプラグイン開発を行っています。

そのため、原則として編集可能なのは、以下のフォルダ配下のファイルのみです。

- app/Plugin/UniCube
- html/template

## Entityの編集について

Entityを編集しデータベース項目に影響がある場合は、プラグインオン・オフ時に適用されるよう以下のファイルに反映してください。

- app/Plugin/UniCube/PluginManager.php

## 画面入力項目の編集について

基本的には、FormTypeを拡張する形で実装してください。

EventListenerから、画面の要素(twig)に対して、setSource()による実装は、原則行わないでください。
もし必要な場合は、最小限の変更に抑えてください。

画面の要素(twig)への操作は、JSでのDOM操作で行うようにしてください。

ただしあまりに大きな画面への変更は、html/template配下にテンプレートを設置し、
そちら自体を参照するような実装を行うことも考慮に入れてください。