---

copyright:
  years: 2019
lastupdated: "2019-05-22"

keywords: IBM Cloud, LogDNA, Activity Tracker, iam, manage user access, viewer

subcollection: logdnaat

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

 
# ユーザー許可をユーザーまたはサービス ID に付与する
{: #iam_view_events}

{{site.data.keyword.iamlong}} (IAM) を使用すると、ユーザーを安全に認証し、{{site.data.keyword.cloud_notm}} ですべてのクラウド・リソースへのアクセスを一貫して制御することができます。 {{site.data.keyword.at_full_notm}} サービスを使用して作業するための最小権限をユーザーまたはサービス ID に付与するには、以下のステップを実行します。 
{:shortdesc}

## 前提条件
{: #iam_view_events_prereq}

ユーザー ID には {{site.data.keyword.at_full_notm}} サービスを管理するための**管理者プラットフォーム権限**が必要です。アカウント管理者にお問い合わせください。アカウント所有者は、ユーザー・アクセスの管理とアカウント・リソースの管理を行う目的で、別のユーザーにアカウントへのアクセス権限を付与できます。[詳細はこちら](/docs/iam?topic=iam-userroles)。



## ステップ 1. アクセス・グループを作成する
{: #iam_view_events_step1}

アクセス・グループを作成するには、以下のステップを実行します。

1. メニュー・バーから、**「管理」** &gt; **「アクセス (IAM)」**をクリックして、**「アクセス・グループ」**を選択します。
2. **「作成」**をクリックします。
3. グループの名前と説明 (オプション) を入力して**「作成」**をクリックします。

**「グループの削除 (Remove group)」**オプションを選択してグループを削除することができます。 グループをアカウントから削除すると、すべてのユーザーとサービス ID がグループから削除され、グループに割り当てられたすべてのアクセス権限が削除されます。
{: note}

CLI を使用してアクセス・グループを作成するには、[ibmcloud iam access-group-create](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_iam#ibmcloud_iam_access_group_create) コマンドを使用します。
```
ibmcloud iam access-group-create GROUP_NAME [-d, --description DESCRIPTION]
```
{: codeblock}



## ステップ 2. イベントを表示する権限を追加する
{: #iam_view_events_step2}

グループをセットアップした後で、共通するアクセス・ポリシーをそのグループに割り当てることができます。 

アクセス・グループに設定するポリシーは、そのグループ内のすべてのエンティティー、ユーザー、およびサービス ID に適用されます。 
{: note}

UI を使用して、またはコマンド・ラインを使ってポリシーを割り当てることができます。

CLI を使用してアクセス・グループ・ポリシーを作成するには、[ibmcloud iam access-group-policy-create](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_commands_iam#ibmcloud_iam_access_group_policy_create) コマンドを使用します。

```
ibmcloud iam access-group-policy-create GROUP_NAME {-f, --file @JSON_FILE | --roles ROLE_NAME1,ROLE_NAME2... [--service-name SERVICE_NAME] [--service-instance SERVICE_INSTANCE] [--region REGION] [--resource-type RESOURCE_TYPE] [--resource RESOURCE] [--resource-group-name RESOURCE_GROUP_NAME] [--resource-group-id RESOURCE_GROUP_ID]}
```
{: codeblock}

ポリシーを定義するときには、プラットフォーム役割とサービス役割を選択する必要があります。
* プラットフォーム管理の役割は、インスタンスの作成と削除、別名、バインディング、および資格情報の管理、およびアクセスの管理を行う能力を含めて、さまざまなアクションをカバーします。 プラットフォームの役割は、管理者、エディター、オペレーター、ビューアーです。 プラットフォーム管理の役割は、アカウント管理サービスにも適用され、ユーザーが、アカウント管理サービスに関して割り当てられた役割に応じて、ユーザーの招待、サービス ID の管理、アクセス・ポリシーの管理、カタログ・エントリーの管理、請求および使用量の追跡を行うことを可能にします。
* サービス・アクセスの役割は、ユーザーまたはサービスの、サービス・インスタンスに関するアクションを実行する能力を定義します。サービス・アクセスの役割は、管理者、ライター、およびリーダーです。

{{site.data.keyword.at_full_notm}} サービスを管理するには、ユーザーに以下の役割が必要です。
* プラットフォーム役割: **ビューアー**。 
* サービス役割: **リーダー**。
[詳細はこちら](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-iam#iam)。



UI を使ってアクセス・グループにポリシーを割り当てるには、以下のステップを実行します。

1. メニュー・バーから、**「管理」** &gt; **「アクセス (IAM)」**をクリックして、**「アクセス・グループ」**を選択します。
2. アクセス権限を割り当てる先のグループの名前を選択します。 
3. **「アクセス・ポリシー」**をクリックします。
4. **「アクセス権限の割り当て (Assign access)」**をクリックします。
5. 権限を付与します。次のオプションのいずれかを選択してください。


### オプション 1. サービスに対する権限を付与する
{: #user_opt1}

以下のステップを実行します。 

1. **「リソースへのアクセス権限の割り当て」**を選択します。
2. **「IBM Cloud Activity Tracker with LogDNA」**を選択します。
3. **「すべての現行地域」**を選択します。
4. **「すべての現行サービス・インスタンス」**を選択します。
5. **「ビューアー」**プラットフォーム役割を選択します。
6. サービス役割**「リーダー」**を選択します。
7. **「割り当て」**をクリックします。

### オプション 2. リソース・グループのコンテキスト内で権限を付与する
{: #user_opt2}

以下のステップを実行します。 

1. **「リソース・グループ内のアクセス権限の割り当て」**を選択します。
2. リソース・グループを選択します。
3. 選択したリソース・グループに対する役割がまだユーザーに付与されていない場合は、**「リソース・グループへのアクセス権限の割り当て」**フィールドで役割を選択します。 

    選択する役割に応じて、ユーザーはダッシュボードでのリソース・グループの表示、リソース・グループ名の編集、またはグループへのユーザー・アクセスの管理を行うことができます。 
    
    リソース・グループ内の {{site.data.keyword.at_full_notm}} サービスへのアクセス権限のみをユーザーに付与する場合は、**「アクセス権限なし」**を選択します。

4. **「IBM Cloud Activity Tracker with LogDNA」**を選択します。
5. **「ビューアー」**プラットフォーム役割を選択します。
6. サービス役割**「リーダー」**を選択します。
7. **「割り当て」**をクリックします。

### オプション 3. ロケーション内で権限を付与する
{: #user_opt3}

プロビジョンできるインスタンスはロケーションごとに 1 つのみです。したがって、地域内のイベントを表示する権限を付与するには、以下のステップを実行します。 

1. **「リソースへのアクセス権限の割り当て」**を選択します。
2. **「IBM Cloud Activity Tracker with LogDNA」**を選択します。
3. ユーザーがイベントを表示する権限を持つ必要のある、地域内のインスタンスを選択します。
4. **「ビューアー」**プラットフォーム役割を選択します。
5. サービス役割**「リーダー」**を選択します。
6. **「割り当て」**をクリックします。


## ステップ 3. ユーザーをアクセス・グループに追加する
{: #iam_view_events_step3}

ユーザーまたはサービス ID を追加することで、グループのセットアップに進みます。

### アクセス・グループへのユーザーの追加
{: #iam_manage_events_step3_user}

以下のステップを実行してユーザーを追加します。

1. メニュー・バーから、**「管理」** &gt; **「アクセス (IAM)」**をクリックして、**「アクセス・グループ」**を選択します。
2. アクセス権限を割り当てる先のグループの名前を選択します。 
3. **「ユーザー」**タブで**「ユーザーの追加」**をクリックします。
4. 追加するユーザーをリストから選択して、**「グループに追加 (Add to group)」**をクリックします。


### アクセス・グループへの サービス ID の追加
{: #iam_manage_events_step3_svcid}

以下のステップを実行してサービス ID を追加します。

1. メニュー・バーから、**「管理」** &gt; **「アクセス (IAM)」**をクリックして、**「アクセス・グループ」**を選択します。
2. アクセス権限を割り当てる先のグループの名前を選択します。 
3. **「サービス ID」**タブをクリックして、**「サービス ID の追加」**をクリックします。
4. 追加する ID をリストから選択して、**「グループに追加 (Add to group)」**をクリックします。


