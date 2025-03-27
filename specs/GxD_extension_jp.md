## Green x Digital コンソーシアム データ連携のための技術仕様拡張

### 2025年3月27日更新

---

## 1. はじめに

このデータモデル拡張の目的は、[CO2可視化フレームワーク](https://www.gxdc.jp/pdf/CO2_VisualizationFrameworkEdition_2.0.1.pdf)（製品ベース算定、組織ベース算定）に準拠した製品カーボンフットプリント(PCF)を、準拠したホストシステム間で相互運用可能な形で交換できるようにすることです。

サプライチェーン全体での脱炭素化を達成するには、自社排出(スコープ1、2)だけでなく、サプライチェーンの上流・下流からの排出(スコープ3)を含むサプライチェーンCO2排出量の正確な把握と削減努力が不可欠です。スコープ3排出量の算出においては、サプライヤーから提供される一次データの利用が重要ですが、以下の2点の課題があります。

1点目は、製品ベース算定の運用負荷の高さから参加企業が少ないことです。製品個別のデータ収集が必要となるため、多くの企業にとってハードルが高くなっています。これに対しGreen x Digital コンソーシアムでは運用負荷の低い組織レベル算定を認め、証書による信頼性担保を条件とすることで、CFP算定への参加を促進します。

2点目は、取引のない企業の製品を使用した際のCO2削減可能量が不明確なため、サプライチェーン全体でのCO2削減の取り組みが難しいことです。これに対しGreen x Digital コンソーシアムではCradle-to-Gate方式をベースとして付加的にGate-to-Gateデータ提供を併用することを認め、製品のライフサイクル全体におけるCO2排出量を把握し、ホットスポット分析を可能にします。これにより、効果的なCO2削減施策の立案・実施が可能となります。

本データモデル拡張を活用することで、サプライチェーン全体のCO2排出量可視化と削減に向けた取り組みを強化できます。詳細な仕様については、次章以降を参照ください。

## 2. 用語

用語集の完全なリストについては、Pathfinder技術仕様の[用語集](https://wbcsd.github.io/data-exchange-protocol/v2/#terminology)セクションを参照してください。

### 製品ベース算定

製品の単位でライフサイクルアセスメント（LCA）や製品のカーボンフットプリントの手法を用いる算定方法

### 組織ベース算定

Scope1・2・3等の組織の排出量データを特定の納品先向けに配分等で切り出す算定方法


## 3. 適合性

Pathfinder Networkとの適合性については、Pathfinder技術仕様の[適合性](https://wbcsd.github.io/data-exchange-protocol/v2/#conformance)セクションを参照してください。


## 4. データモデル拡張

このセクションでは、Pathfinder Networkに準拠した製品カーボンフットプリントのデータモデル拡張を規定します。このデータモデル拡張は、Pathfinderデータモデルで規定されている内容に加えて、追加情報を含みます。


### 4.1 データ型: 算定方法(`calcMethod`)

| プロパティ | 型 | 要求レベル | 説明 |
|---|---|---|---|
| `calcMethod` | String | M | 算定方法。0: 製品ベース算定、1: 組織ベース算定 |

### 4.2 データ型: CO2可視化フレームワークエディション(`FWedition`)

| プロパティ | 型 | 要求レベル | 説明 |
|---|---|---|---|
| `FWedition` | String | M | 参照したCO2可視化フレームワークのEdition。CO2可視化フレームワーク Edition 2.0 を参照した場合は 「2.0」。 |


### 4.3 データ型: 組織ベース算定 (`organization`)

| プロパティ | 型 | 要求レベル | 説明 |
|---|---|---|---|
| `scope3Category` | Array<Number> | O | 算定対象カテゴリ（組織ベース算定用） |
| `scope1DistributionLevel` | String | M | 配分レベル Scope1（組織ベース算定用） |
| `scope2DistributionLevel` | String | M | 配分レベル Scope2（組織ベース算定用） |
| `scope3DistributionLevel` | String | M | 配分レベル Scope3（組織ベース算定用） |
| `scope1DistributionIndex` | String | O | 配分の指標 Scope1（組織ベース算定用） |
| `scope2DistributionIndex` | String | O | 配分の指標 Scope2（組織ベース算定用） |
| `scope3DistributionIndex` | String | O | 配分の指標 Scope3（組織ベース算定用） |
| `distributionLevelComment` | String | O | 配分レベル記述欄 |
| `distributionIndexComment` | String | O | 配分の指標記述欄 |


### 4.4 データ型: 証書情報(`certificate`)

| プロパティ | 型 | 要求レベル | 説明 |
|---|---|---|---|
| `certificateAmount` | String | O | 証書使用量（含む再エネ電力由来J-クレジット） |
| `certificateType` | String | O | 証書種類（含む再エネ電力由来J-クレジット） |


### 4.5 データ型: Gate-to-Gate排出量(`gateToGate`)

| プロパティ | 型 | 要求レベル | 説明 |
|---|---|---|---|
| `gateToGateFossilGhgEmissions` | String | O | Gate-to-Gate排出量（生物由来の排出と除去を含まない） |
| `gateToGateBiogenicCarbonContent` | String | O | Gate-to-Gate排出量（生物由来の排出と除去を含む） |
| `unitaryProductAmountComment` | String | O | 製品量記述欄。「製品量」と「宣言単位」についての説明 |


## 5. 備考

このドキュメントは、Green x Digital コンソーシアムの[データ連携のための技術仕様 Version 2.0](https://www.gxdc.jp/pdf/technical_spec_2.0.pdf)に基づき、データモデル拡張を定義します。詳細は上記のリンクを参照してください。

## 6.連絡先
Green x Digital
green_digital@jeita.or.jp