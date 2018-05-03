---
title: 'クイック スタート: Visual Studio を使用して Python Web アプリを作成する'
description: このクイック スタートでは、Visual Studio と Flask フレームワークを使用し、Pythonで簡単な Web アプリを作成します。
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 3c57dab3ac6ca4ee28b568a6fb8004f5559dfed2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>クイック スタート: Visual Studio を使用して初めての Python Web アプリを作成する

Python IDE としての Visual Studio を紹介する、この 5 ～ 10 分のクイック スタートでは、Flask フレームワークに基づいて Python Web アプリを作成します。 別個の部分からなる手順を通してプロジェクトを作成することが、Visual Studio の基本機能の学習に役立ちます。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)に移動し、無料試用版をインストールしてください。 インストーラーでは、必ず **[Python 開発]** ワークロードを選択します。

## <a name="create-the-project"></a>プロジェクトの作成

以降の手順では、アプリケーションのコンテナーとして機能する空のプロジェクトを作成します。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーから、**[ファイル] > [新規作成] > [プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスの右上にある検索ボックスに "Python Web Project" と入力し、真ん中の一覧にある **[Web プロジェクト]** を選択し、"HelloPython" のような名前をプロジェクトに付け、**[OK]** を選択します。

    ![Python Web プロジェクトが選択されている [新しいプロジェクト] ダイアログ](media/quickstart-python-00-web-project.png)

    Python のプロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスを取り消し、上部のメニュー バーから **[ツール] > [ツールと機能を取得]** の順に選択して、**Visual Studio インストーラー**を開きます。 **[Python 開発]** ワークロードを選び、**[変更]** を選びます。

    ![Visual Studio インストーラーの [Python 開発] ワークロード](../python/media/installation-python-workload.png)

1. 右側のウィンドウの**ソリューション エクスプローラー**で、新しいプロジェクトが開きます。 この時点のプロジェクトは、他のファイルが含まれていないため空です。

    ![新しく作成された空のプロジェクトが表示されているソリューション エクスプローラー](media/quickstart-python-01-empty-project.png)

**質問: Visual Studio で Python アプリケーション用のプロジェクトを作成する利点は何ですか。**

**回答**: 通常、Python アプリケーションはフォルダーとファイルのみを使って定義されますが、アプリケーションが大きくなり、おそらく自動生成されたファイル、Web アプリケーション用 JavaScript などが含まれるようになると、この単純な構造が面倒になる可能性があります。 Visual Studio のプロジェクトは、このような複雑さを管理するのに役立ちます。 プロジェクト (*.pyproj* ファイル) には、プロジェクトに関連付けられたすべてのソース ファイルとコンテンツ ファイルの識別、各ファイルのビルド情報の格納、ソース管理システムと統合するための情報の保持、論理コンポーネントへのアプリケーションの整理の補助などの機能があります。

**質問: ソリューション エクスプローラーに表示される "ソリューション" とは何ですか。**

**回答**: Visual Studio のソリューションとは、1 つまたは複数の関連プロジェクトを 1 つのグループとして管理できるコンテナーであり、プロジェクトに固有ではない構成設定が格納されます。 ソリューションの中のプロジェクトは互いに参照できます。プロジェクトを 1 つ (Python アプリ) 実行すると、2 つ目のプロジェクト (Python アプリで使用される C++ 拡張など) が自動的に作成されたりします。

## <a name="install-the-flask-library"></a>Flask ライブラリをインストールする

Python の Web アプリは、ほぼ常に、Web 要求のルーティングや応答の整形といった低レベルの詳細を処理するために、多くの使用可能な Python ライブラリのいずれかを使います。 Visual Studio ではこの目的のために、Web アプリ用にさまざまなテンプレートを用意しています。このクイック スタートではそのうちの 1 つを後で使用します。

ここでは、次の手順で、Visual Studio によってこのプロジェクトに使用される既定の "グローバル環境" に Flask ライブラリをインストールします。

1. プロジェクトの **[Python 環境]** ノードを展開して、プロジェクトの既定の環境を表示します。

    ![既定の環境が表示されているソリューション エクスプローラー](media/quickstart-python-02-default-environment.png)

1. 環境を右クリックして、**[Python パッケージのインストール]** を選択します。 このコマンドを選ぶと、**[Python 環境]** ウィンドウの **[パッケージ]** タブが開きます。

1. 検索フィールドに "flask" と入力し、**[pip install flask from PyPI]\(PyPI から flask の pip インストール\)** を選択します。 管理者特権に関するすべてのプロンプトに同意し、Visual Studio の **[出力]** ウィンドウで進行状況を確認します。 (グローバル環境のパッケージ フォルダーが *C:\Program Files* のように保護された領域内にある場合は、昇格のプロンプトが表示されます)。

    ![Flask ライブラリをインストールする](media/quickstart-python-03-install-package.png)

1. インストールが済むと、**ソリューション エクスプローラー**の環境にライブラリが表示されます。これは、Python コードでライブラリを使用できることを意味します。

    ![Flask ライブラリがインストールされました](media/quickstart-python-04-package-installed.png)

> [!Note]
> 開発者は通常、グローバル環境にライブラリをインストールするのではなく、特定のプロジェクトのライブラリをインストールする "仮想環境" を作成します。 Visual Studio のテンプレートによって通常、このオプションが与えられます。それについては、「[クイック スタート - Visual Studio のテンプレートから Python プロジェクトを作成する](../python/quickstart-02-python-in-visual-studio-project-from-template.md)」に説明があります。

**質問: 利用できる他の Python パッケージの詳細はどこで確認できますか。**

**回答**: [Python Package Index](https://pypi.python.org/pypi) を参照してください。

## <a name="add-a-code-file"></a>コード ファイルの追加

最小限の Web アプリを実装するための Python コードを追加する準備ができました。

1. **ソリューション エクスプローラー**でプロジェクトを右クリックして、**[追加] > [新しい項目]** を選択します。

1. 表示されるダイアログ ボックスで、**[空の Python ファイル]** を選択し、「*app.py*」という名前を付けて、**[追加]** を選択します。 エディター ウィンドウでファイルが自動的に開きます 

1. 次のコードをコピーして、*app.py* に貼り付けます。

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. お気付きかもしれませんが、**[追加]、[新しい項目]** ダイアログ ボックスの順に選択すると、Python プロジェクトに追加できる他の種類のファイルがたくさん表示されます。Python クラス、Python パッケージ、Python 単体テスト、*web.config* ファイルなどです。 一般的に、項目テンプレートと呼ばれているこのようなテンプレートは、便利なボイラープレート コードで簡単にファイルを作成する優れた方法です。

**質問: Flask の詳細はどこで確認できますか。**

**回答**: Flask 文書を参照してください。まずは [Flask クイック スタート](http://flask.pocoo.org/docs/0.12/quickstart/#quickstart)からお読みください。

## <a name="run-the-application"></a>アプリケーションの実行

1. **ソリューション エクスプローラー**で *app.py* を右クリックし、**[スタートアップ ファイルとして設定]** を選択します。 このコマンドによって、アプリの実行時、Python で起動するコード ファイルが特定されます。

    ![ソリューション エクスプローラーでプロジェクトのスタートアップ ファイルを設定](media/quickstart-python-05-set-as-startup-file.png)

1. **ソリューション エクスプローラー**でプロジェクトを右クリックして、**[プロパティ]** を選択します。 次に、**[デバッグ]** タブを選び、**[ポート番号]** プロパティを `4449` に設定します。 この手順によって、Visual Studio では、コードの `app.run` 引数に合わせ、`localhost:4449` でブラウザーが起動します。

1. **[デバッグ]、[デバッグなしで開始]** (**Ctrl**+**F5**) の順に選択し、変更をファイルに保存し、アプリを実行します。

1. コマンド ウィンドウに "* Running in https://localhost:4449/" というメッセージが表示された後、`localhost:4449` でブラウザー ウィンドウが開き、"Hello, Python!" というメッセージが表示されます。 コマンド ウィンドウにステータス 200 で GET 要求も表示されます。

    ブラウザーが自動的に開かない場合は、任意のブラウザーを起動して `localhost:4449` に移動します。

    コマンド ウィンドウに Python 対話型シェルのみが表示される場合、または画面でそのウィンドウが短時間点滅する場合は、上記の手順 1 でスタートアップ ファイルとして *app.py* を設定してあるかどうかを確認してください。

1. `localhost:4449/hello` に移動し、`/hello` リソースのデコレーターも機能することをテストします。 再び、コマンド ウィンドウには GET 要求が表示されます。ステータスは 200 です。 他の URL も試し、コマンド ウィンドウにステータス コード 404 が表示されることを確認してください。

1. コマンド ウィンドウを閉じてアプリを停止してから、ブラウザー ウィンドウを閉じます。

**質問: デバッグなしで開始コマンドとデバッグの開始の違いとは何ですか。**

**回答**: **デバッグの開始**を使用し、[Visual Studio デバッガー](../python/debugging-python-in-visual-studio.md)に関連してアプリを実行します。ブレークポイントを設定したり、変数を調べたり、コードを行ごとにステップ実行したりできます。 さまざまなフックがデバッグを可能にするため、デバッガーではアプリの実行が遅くなることがあります。 対照的に、**デバッグなしで開始**では、デバックという文脈なしで、コマンド ラインから実行したかのように、アプリが直接実行されます。また、ブラウザーが自動的に起動し、プロジェクト プロパティの **[デバッグ]** タブに指定されている URL に移動します。

## <a name="next-steps"></a>次の手順

Visual Studio から初めての Python アプリを実行できました。おめでとうございます。Python IDE として Visual Studio を使用することについて少しばかり学習しました。

このクイック スタートで実行した手順はかなり汎用的です。これは自動化できるし、自動化すべきであると思ったことでしょう。 そのような自動化は、Visual Studio プロジェクト テンプレートの役目です。 下のボタンを選択し、デモをご覧ください。この記事で作成したものと似た Web アプリが作成されます。ただし、手順は少なくなっています。

> [!div class="nextstepaction"]
> [クイック スタート - テンプレートを使用して Python プロジェクトを作成する](../python/quickstart-02-python-in-visual-studio-project-from-template.md)

対話型ウィンドウの使用、デバッグ、データの視覚化、Git の操作など、Visual Studio での Python についての詳細なチュートリアルを続行するには、下のボタンを選んでください。

> [!div class="nextstepaction"]
> [チュートリアル: Visual Studio での Python の概要](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

Visual Studio のその他の機能は下のリンクからご覧いただけます。

- [Visual Studio での Python Web アプリ テンプレート](../python/python-web-application-project-templates.md)について学習する
- [Python のデバッグ](../python/debugging-python-in-visual-studio.md)について学習する
- 全般的な [Visual Studio の IDE](../ide/visual-studio-ide.md) について学習する