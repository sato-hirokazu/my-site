---
path: "/post-one"
cover: "./blocks.jpg"
date: "2018-10-15"
title: "AWS1"
published: true
tags: ['website', 'react', 'other']
---

A社ではAWSのRedshiftを利用してBIシステムを構築しようとしています。 あなたはソリューションアーキテクトとしてRedshiftクラスターを費用対効果の高い方法で使用することが要求されています。

この要件を満たすため
クラスターに対するスナップショットのうち不必要な設定を削除する


Redshiftではスナップショット用に無料ストレージを提供してますが、ストレージ容量が超過すると課金が発生します。スナップショットの空き容量が上限に達すると課金される仕組みとなっています。 このため、自動スナップショットを保存し、保存期間日数を見直すことで、不要になった手動スナップショットを削除する必要があります。したがって、オプション１が正解となります。



オプション２は不正解です。Amazon Redshiftにおいて拡張された VPC ルーティングを使用すると、Amazon Redshift はクラスターとデータリポジトリ間のすべての COPY と UNLOAD トラフィックが Amazon VPC を通るよう強制されます。この設定の有無はコストには影響を与えません。

オプション３は不正解です。オンデマンドインスタンスの代わりに、スポットインスタンスを利用すると処理が停止する可能性が出てくるため不適切な設定となっております。Amazon Redshiftで利用できるのはリザーブドインスタンスです。Redshift は 1 年間または 3 年間の契約を結ぶことにより、オンデマンド料金に比べて最大 75 % のコストを節約できます。

オプション４は不正解です。CloudWatchメトリクスは無料で利用できますが、カスタムメトリクスを利用すると有料となります。不必要なCloudWatchのメトリクス設定を削除するだけでは有料分の削除とはならないため不適切です。



あなたの会社は画像配信アプリケーションを運用しています。画像配信を最適にするためにCloudFrontを利用していますが、コンテンツがエッジ側にない場合にどのような処理が発生するでしょうか。

次の中で妥当なCloudFront処理を選択してください。
CloudFrontがオリジンサーバーにアクセスしてエッジにデータを取得する


CloudFrontはユーザーから最も近いエッジロケーションにデータをキャッシュするコンテンツ配信ネットワーク（CDN）サービスであり、データ取得の待ち時間を短縮します。 データがエッジロケーションに存在しない場合は、データをオリジンサーバーから取得してから配信する可能性がありますが、次の配信以降はエッジロケーションにあるキャッシュを利用してデータが配信されます。したがって、オプション２が正解となります。



オプション１は不正解です。要求を別のエッジロケーションから配信する処理方法はありません。CloudFrontはユーザーに近いエッジからの配信を実施します。したがって、配信先のユーザーに適したエッジに配信キャッシュがない場合は、オリジンサーバーにデータを取得しに行きます。

オプション３は不正解です。適切なデータが配置されていないことを理由としてユーザーが404エラーを受け取ることはありません。ユーザーの近くのエッジに配信キャッシュがない場合は、オリジンサーバーにデータを取得しに行きます。

オプション４は不正解です。CloudFrontが要求をストックして、エッジにデータがくるまで待機することはありません。



あなたは自社インフラの可用性を高めるためにAuto Scalingグループを設定しました。 しかしながら、設定に問題があり、Auto Scalingの設定条件に合致した場合でもグループは30時間以上もの間、インスタンスを起動することができませんでした。

この場合に想定されるAuto Scalingで実行される処理を選択してください。
<p>Auto Scalingは起動プロセスを停止する。</p>

Auto Scalingがインスタンス起動時に問題が発生すると、AutoScalingはグループ内で実施されている1つ以上のプロセスを中断して、あなたは、そのプロセスは任意の時期に再開することができます。プロセスを 中断することによって、ユーザーが設定上の問題を解析することができます。したがって、オプション２が正解となります。



企業Bは3TBボリュームデータをオンプレミスのリポジトリ内に所有しており、大量の印刷ファイルを保存しています。 このリポジトリは年間500 GBの容量が増加しており、単一の論理ボリュームとして利用していく必要があります。 あなたはソリューションアーキテクトとして、頻繁にアクセスされるデータへの最適な応答時間を維持しつつ、ローカルストレージ容量の制約を回避するために、このレポジトリーをS3ストレージに拡張することになりました。S3をプライマリーに利用していく予定です。

次のうちで、どのAWS Storage Gateway構成が要件を満たしていますか？

<p>S3への移転スケジュールが設定されたスナップショットを利用するキャッシュ型ボリューム</p>


ストレージゲートウェイのキャッシュ型ボリュームを使用すると、頻繁にアクセスされるデータをローカル環境に保持しながら、S3をプライマリデータストレージとして使用できます。したがって、オプション１が正解となります。

その名の通り、Storage Gatewayのボリューム型ゲートウェイではスケジュールされたスナップショットというものが機能として存在しています。スナップショット取得をスケジューリングして管理する方式となっています。

【参照】

https://docs.aws.amazon.com/ja_jp/storagegateway/latest/userguide/managing-volumes.html#SchedulingSnapshot



キャッシュ型ボリュームは、オンプレミスのストレージインフラストラクチャをスケールする必要性を最小限に抑えます。同時に、アプリケーションは引き続き頻繁にアクセスするデータへの低レイテンシーなアクセスが可能になります。作成できるストレージボリュームのサイズは最大 32TiB で、それを iSCSI デバイスとしてオンプレミスのアプリケーションサーバーにアタッチすることが可能です。ゲートウェイは、保存データを Amazon S3 に作成されたストレージボリュームに保存し、最近読み込まれたデータはオンプレミスのストレージゲートウェイのキャッシュに保持して、バッファストレージにアップロードします。



オプション２は不正解です。ストレージゲートウェイの保管型ボリュームを使用すると、ローカルストレージをプライマリーとして利用し、そのデータを非同期に S3にバックアップします。今回はキャッシュ型ボリュームが要件に合致しています。

オプション３は不正解です。ストレージゲートウェイによるハイブリッド構成用にはS3ストレージを利用します。Glacierは不適切です。かつ、Glacierは中長期に利用頻度が低いファイルを保存する際に用いられるため、オプション３は今回の要件には不適切です。

オプション４は不正解です。仮想テープライブラリーはテープ形式のバックアップに利用されるものであり、オプション４は不適切です。

