---
title: Visual Studio で C++ DLL 用の単体テストを作成する
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 0d79c8a57a58e92f826a9d6bf48ac15213a2f58e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382669"
---
# <a name="write-unit-tests-for-c-dlls-in-visual-studio"></a>Visual Studio で C++ DLL 用の単体テストを作成する

 テストする関数をエクスポートするかどうかによって、DLL コードをテストする方法はいくつかあります。 次のいずれかの方法を選択してください。

 **DLL からエクスポートされた関数のみを単体テストで呼び出す:** 「[Visual Studio で C/C++ 用の単体テストを作成する](writing-unit-tests-for-c-cpp.md)」で説明されているように、別個のテスト プロジェクトを追加します。 このテスト プロジェクトで、DLL プロジェクトへの参照を追加します。

 手順「[テスト プロジェクトからエクスポートされた関数を参照するには](#projectRef)」に移動します。

 **DLL は .exe ファイルとしてビルドされます。** 別個のテスト プロジェクトを追加します。 これを出力オブジェクト ファイルにリンクします。

 手順「[テストをオブジェクトまたはライブラリ ファイルにリンクするには](#objectRef)」に移動します。

 **DLL からエクスポートされない非メンバー関数を単体テストで呼び出し、DLL はスタティック ライブラリとしてビルドできる:** *.lib* ファイルとしてコンパイルされるように、DLL プロジェクトを変更します。 テスト対象のプロジェクトを参照する、別のテスト プロジェクトを追加します。

 この方法には、エクスポートされないメンバーをテストで使用できる一方で、独立したプロジェクトにテストが保持されるという利点があります。

 「[DLL をスタティック ライブラリに変更するには](#staticLink)」の手順に移動します。

 **単体テストはエクスポートされない非メンバー関数を呼び出す必要があり、コードをダイナミック リンク ライブラリ (DLL) としてビルドする必要があります。** 製品コードと同じプロジェクトに単体テストを追加します。

 「[同じプロジェクトに単体テストを追加するには](#sameProject)」の手順に移動します。

## <a name="create-the-tests"></a>テストを作成する

###  <a name="staticLink"></a> DLL をスタティック ライブラリに変更するには

-   DLL プロジェクトによってエクスポートされないメンバーをテストで使う必要があり、テスト対象のプロジェクトがダイナミック ライブラリとしてビルドされる場合は、これをスタティック ライブラリに変換することを検討します。

    1.  **ソリューション エクスプローラー**で、テスト対象プロジェクトのショートカット メニューの **[プロパティ]** をクリックします。 プロジェクトの**プロパティ** ウィンドウが開きます。

    2.  **[構成プロパティ]** > **[全般]** の順に選びます。

    3.  **[構成の種類]** を **[スタティック ライブラリ (.lib)]** に設定します。

 手順「[テストをオブジェクトまたはライブラリ ファイルにリンクするには](#objectRef)」を続行します。

###  <a name="projectRef"></a> テスト プロジェクトからエクスポートされた DLL 関数を参照するには

-   テストする関数が DLL プロジェクトからエクスポートされる場合は、テスト プロジェクトからコード プロジェクトへの参照を追加できます。

    1.  ネイティブ単体テスト プロジェクトを作成します。

        1.  **[ファイル]** メニューで、**[新規]** > **[プロジェクト]** > **[Visual C++]** > **[テスト]** > **[C++ 単体テスト プロジェクト]** の順に選びます。

    2.  **ソリューション エクスプローラー**で、テスト プロジェクトのショートカット メニューの **[参照]** を選びます。 プロジェクトの**プロパティ** ウィンドウが開きます。

    3.  **[共通プロパティ]** > **[Framework と参照]** の順に選び、**[新しい参照の追加]** ボタンを選びます。

    4.  **[プロジェクト]** をクリックし、テスト対象のプロジェクトを選択します。

         **[追加]** ボタンをクリックします。

    5.  テスト プロジェクトのプロパティで、テスト対象プロジェクトの場所をインクルード ディレクトリに追加します。

         **[構成プロパティ]** > **[VC++ ディレクトリ]** > **[インクルード ディレクトリ]** の順に選びます。

         **[編集]** をクリックし、テスト対象プロジェクトのヘッダー ディレクトリを追加します。

 「[単体テストを作成する](#addTests)」に進みます。

###  <a name="objectRef"></a> オブジェクト ファイルまたはライブラリ ファイルにテストをリンクするには

-   テストする関数が DLL でエクスポートされない場合は、出力された *.obj* ファイルまたは *.lib* ファイルをテスト プロジェクトの依存関係に追加できます。

    1.  ネイティブ単体テスト プロジェクトを作成します。

        1.  **[ファイル]** メニューで、**[新規]** > **[プロジェクト]** > **[Visual C++]** > **[テスト]** > **[ネイティブ単体テスト プロジェクト]** の順に選びます。

    2.  **ソリューション エクスプローラー**で、テスト プロジェクトのショートカット メニューの **[プロパティ]** を選びます。

    3.  **[構成プロパティ]** > **[リンカー]** > **[入力]** > **[追加の依存ファイル]** の順に選びます。

         **[編集]** をクリックし、**.obj** ファイルまたは **.lib** ファイルの名前を追加します。 完全パス名は使用しないでください。

    4.  **[構成プロパティ]** > **[リンカー]** > **[全般]** > **[追加のライブラリ ディレクトリ]** の順に選びます。

         **[編集]** をクリックし、**.obj** ファイルまたは **.lib** ファイルのディレクトリ パスを追加します。 一般的にパスは、テスト対象プロジェクトのビルド フォルダー内になります。

    5.  **[構成プロパティ]** > **[VC++ ディレクトリ]** > **[インクルード ディレクトリ]** の順に選びます。

         **[編集]** をクリックし、テスト対象プロジェクトのヘッダー ディレクトリを追加します。

 「[単体テストを作成する](#addTests)」に進みます。

###  <a name="sameProject"></a> 同じプロジェクトに単体テストを追加するには

1.  単体テストに必要なヘッダーおよびライブラリ ファイルが含まれるように、製品コード プロジェクトのプロパティを変更します。

    1.  **ソリューション エクスプローラー**で、テスト対象プロジェクトのショートカット メニューの **[プロパティ]** を選びます。 プロジェクトの**プロパティ** ウィンドウが開きます。

    2.  **[構成プロパティ]** > **[VC++ ディレクトリ]** の順に選びます。

    3.  インクルード ディレクトリおよびライブラリ ディレクトリを編集します。

        |ディレクトリ|プロパティ|
        |-|-|
        |**インクルード ディレクトリ** | **$(VCInstallDir)UnitTest\include;$(IncludePath)**|
        |**ライブラリ ディレクトリ** | **$(VCInstallDir)UnitTest\lib;$(LibraryPath)**|

2.  C++ 単体テスト ファイルを追加します。

    -   **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**[追加]** > **[新しい項目]** > **[C++ 単体テスト]** の順に選びます。

 「[単体テストを作成する](#addTests)」に進みます。

##  <a name="addTests"></a> 単体テストを作成する

1.  各単体テスト コード ファイルに、テスト対象プロジェクトのヘッダー用に `#include` ステートメントを追加します。

2.  単体テスト コード ファイルに、テスト クラスとメソッドを追加します。 例:

    ```cpp
    #include "stdafx.h"
    #include "CppUnitTest.h"
    #include "MyProjectUnderTest.h"
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;
    namespace MyTest
    {
      TEST_CLASS(MyTests)
      {
      public:
          TEST_METHOD(MyTestMethod)
          {
              Assert::AreEqual(MyProject::Multiply(2,3), 6);
          }
      };
    }
    ```

## <a name="run-the-tests"></a>テストを実行

1.  **[テスト]** メニューで、**[Windows]**、**[テスト エクスプローラー]** の順に選択します。

1. ウィンドウに一部のテストしか表示されない場合は、次の方法でテスト プロジェクトをビルドします。**ソリューション エクスプローラー**で、該当するノードを右クリックし、**[ビルド]** または **[リビルド]** を選択します。

1.  **テスト エクスプローラー**で、**[すべて実行]** を選択するか、または実行する特定のテストを選択します。 ブレークポイントを有効にした場合のデバッグ モードでのテストの実行など他のオプションについては、テストを右クリックします。

## <a name="see-also"></a>関連項目

- [C/C++ 用の単体テストの記述](writing-unit-tests-for-c-cpp.md)
- [Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Reference](../test/microsoft-visualstudio-testtools-cppunittestframework-api-reference.md)
- [ネイティブ コードをデバッグする](../debugger/debugging-native-code.md)
- [チュートリアル: ダイナミック リンク ライブラリの作成と使用 (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [インポートとエクスポート](/cpp/build/importing-and-exporting)
- [クイック スタート: テスト エクスプローラーによるテスト駆動開発](../test/quick-start-test-driven-development-with-test-explorer.md)
