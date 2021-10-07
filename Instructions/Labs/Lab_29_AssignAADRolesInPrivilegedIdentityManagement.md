---
lab:
    title: '29 - Azure AD ロール用に Privileged Identity Management を構成する'
    learning path: '04'
    module: 'モジュール 03 - 特権アクセスの計画と実装を行う'
---

# ラボ 29: Privileged Identity Management で Azure AD ロールを割り当てる

## ラボ シナリオ

グローバル管理者は、Azure Active Directory (Azure AD) を使用して、永続的な Azure AD 管理者ロールの割り当てを行うことができます。こうしたロールの割り当ては、Azure portal または PowerShell のコマンド を使用して作成できます。

永続的な管理ロールの割り当ては、特権ロール管理者が Azure AD Privileged Identity Management (PIM) サービスを使用して行うこともできます。さらに、特権ロール管理者は、ユーザーを Azure AD 管理者ロールの候補にすることもできます。管理者候補は必要なときにロールをアクティブ化できます。作業が完了すると、そのアクセス許可は期限切れになります。

#### 推定時間: 15 分

## ロールの割り当て

ユーザーを Azure AD 管理者ロールの候補にするには、次の手順を実行します。

1. グローバル管理者アカウントを使用して、[https://portal.azure.com](https://portal.azure.com) にサインインします。

1. **「Azure AD Privileged Identity Management」** を検索してから選択します。

1. Privileged Identity Management ブレードの左側のナビゲーションで **「Azure AD ロール」** を選択します。

1. 「クイック スタート」ページの左側のナビゲーションで **「ロール」** を選択します。

1. 上部のメニューで **「+ 割り当ての追加」** を選択します。

    ![「割り当ての追加」メニューが強調表示された Azure AD ロールを表示している画面イメージ](./media/lp4-mod3-pim-assign-role.png)

1. 「割り当ての追加」ブレードの **「メンバーシップ」** タブで設定を確認します。

1. **「ロールの選択」** メニューを選択し、**「コンプライアンス管理者」** を選択します。

1. **「メンバーの選択」** で **「メンバーが選択されていません」** をクリックします。

1. 「メンバーの選択」ウィンドウで、**Miriam Graham** を選択してから、**「選択」** を選択します。

    ![選択したメンバーが強調表示された「メンバーの選択」ウィンドウを表示している画面イメージ](./media/lp4-mod3-pim-add-role-assignment.png)

1. 「割り当ての追加」ブレードで **「次へ」** を選択します。

1. **「設定」** タブの **「割り当ての種類」** で、使用可能なオプションを確認します。このタスクでは、既定の設定を使用します。

    - 有資格者（対象）に割り当てられたユーザーは、ロールをアクティブにするためにいくつかのアクションが要求されます。アクションには、多要素認証 (MFA) チェックの実行、業務上の妥当性の指定、指定された承認者に対する承認要求などがあります。
    - アクティブに割り当てられたユーザーは特に何もする必要はありません。割り当てられた瞬間からロールを行使することができます。

1. 残りの設定を確認してから、**「割り当て」** を選択します。

## Miriam でログインする

1. InPrivate ブラウザー ウィンドウを開きます。
2. Azure portal (https://portal.azure.com) に接続します。
3. Miriam でログインします。

| フィールド | 値 |
| :--- | :--- |
| ユーザー名 | **MiriamG@** `<<your domain.onmicrosoft.com>>` |
| パスワード | 管理者と同じです |

5. **「Azure へようこそ」ダイアログ** を閉じます。

6. **Azure Active Directory** の管理画面に移動します。

7. **「Overview」** ページで、**「My Feed」** を探します。

8. **Miriam Graham** の名前を選択します。 これにより、Miriam のプロフィール ページが開きます。

9. **「Assigned roles（割り当てられたロール）」** を選択してから、**「Eligible assignments（資格のある割り当て）」** を選択します。

10. Miriam が**Compliance Administrator(コンプライアンス管理者)**のロールの対象者になっていることがわかります。

## Azure AD ロールをアクティブにする

Azure AD ロールを使用する場合は、Privileged Identity Management で **「My roles（自分のロール）」** を開いてアクティブ化を要求できます。

1. 「**Privileged Identity Management**」 を検索して、開きます。

1. 「Privileged Identity Management」ブレードの左側のナビゲーションで **「My roles(自分のロール)」** を選択します。

1. 「My roles」ブレードで、Eligible assignments(資格のある割り当て)の一覧を確認します。

    ![資格のあるロールの割り当てと「自分のロール」が強調表示されているアプリ ロールを示す画面イメージ](./media/lp4-mod3-my-roles.png)

1. 「Compliance Administrator(コンプライアンス管理者ロール)」行で、右端の **「Activate（アクティブ化）」** を選択します。

1. 「アクティブ化 - コンプライアンス管理者」ウィンドウで **「Aditional verification required（追加の確認が必要）」** をクリックし、指示に従って追加のセキュリティ情報の追加を行います。

    ![コンプライアンス管理者をアクティブにするためのポップアップを表示している画面イメージ](./media/lp4-mod3-pim-activate-role.png)

    **検証** - 現在のラボ環境構成に基づいて、MFA を構成し、正常にログインする必要があります。

1. 追加のセキュリティ確認を完了したら、「Activate - Compliance Administrator」ウィンドウの **「Reson」** ボックスに、適当に理由を入力します。

    **重要な注意** - 最小特権の原則として、アカウントは必要な期間だけアクティブ化する必要があります。  1.5 時間必要な場合は 2 時間に設定します。午後 3 時から作業を開始したい場合は、Custom Activation start timeを選択して、開始時間を指定します。

1. **「Activate」** を選択します。

1. **Privileged Identity Management** ページに戻り、**My request** をクリックします。

1. 一覧に自分のリクエストが表示されていることを確認します。

このロールのアクティベーションには管理者の承認が必要なため、まだアクティベーションは完了していません。

## Miriam のロール割り当てを承認する

既存のロールの割り当てを更新するには、次の手順を実行します。

1. 管理者で、「Privileged Identity Management」 を開きます。

1. **申請の承認** を開きます。

1. **ロールのアクティブ化に関する要求** に Miriam からのリクエストが表示されていることを確認します。理由も確認してください。

1. Miriam からのリクエストをチェックし、「**承認**」をクリックします。

1. 承認の理由の入力が求められるので、理由を入力して **確認** をクリックします。

これで、Miriam は時限的にコンプライアンス管理者になりました。指定した時間が経過すると、自動的に「対象者（有資格者）」に戻されます。

Miriam でログインして、再度 Privileged Identity Management を開き Azure AD roles を確認すると、「**Active assignments**」に **Compliance Administrator** が表示されていることがわかります。

## 制限スコープがあるロールを割り当てる

特定のロールでは、付与されるアクセス許可の範囲を **管理単位（管理ユニット）**、**サービス プリンシパル**、または**アプリケーション**に制限することができます。この手順は、管理単位のスコープを持つロールを割り当てる場合の例です。

1. 管理者アカウントとして Azure portal を開きます。

1. 「Privileged Identity Management」ブレードに移動し、左側のナビゲーション メニューで **「Azure AD ロール」** を選択します。

1. 「**ロール**」を選択します。

1. 「ロール」ブレードの上部のメニューで **「+ 割り当ての追加」** を選択します。

1. 「割り当ての追加」ブレードで **「ロールの選択」** メニューを選択し、**「ユーザー管理者」** を選択します。

1. **「スコープの種類」** メニューを選択し、使用可能なオプションを表示して、**管理単位** が選択できることを確認します。

>[!ヒント]
>管理単位のスコープの種類の詳細については、[https://docs.microsoft.com/ja-jp/azure/active-directory/roles/admin-units-manage](https://docs.microsoft.com/ja-jp/azure/active-directory/roles/admin-units-manage) を参照してください。

1. **「キャンセル」** を選択します。

