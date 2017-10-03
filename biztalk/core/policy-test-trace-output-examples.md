---
title: "Exemples de sortie de Trace de Test de stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, policies
- policies, testing
- testing, examples
ms.assetid: 92e1dc7f-1a8d-41a5-84b6-46d5ad9f2ef2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3678769dffa03bb77c3e86fef02998a354b1fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="policy-test-trace-output-examples"></a>Exemples de résultat du suivi du test de stratégies
Cette section contient des exemples de résultat du test de stratégies pour différents types de faits.  
  
## <a name="net-class"></a>Classe .Net  
 Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :  
  
```  
IF test.get_ID > 0  
THEN <do something>  
```  
  
 **Sortie :**  
  
 TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/16/2004 9:50:28 : 00  
  
 ACTIVITÉ DES FAITS 3/16/2004 9:50:28 : 00  
  
 Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : MyTest.test  
  
 Identificateur de l’Instance de l’objet : 872  
  
 TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/16/2004 9:50:28 : 00  
  
 Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Nom du groupe de règles : LoanProcessing  
  
 Expression de test : MyTest.test.get_ID > 0  
  
 Valeur de l’opérande gauche : 100  
  
 Valeur de l’opérande droite : 0  
  
 Résultat de test : True  
  
 METTRE À JOUR DE AGENDA 3/16/2004 9:50:28 : 00  
  
 Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/16/2004 9:50:28 : 00  
  
 Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/16/2004 9:50:28 : 00  
  
 Identificateur de l’Instance du moteur de règles : 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : MyTest.test  
  
 Identificateur de l’Instance de l’objet : 872  
  
## <a name="dataconnectiontypeddatarow"></a>DataConnection/TypedDataRow  
 Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 **Sortie :**  
  
 TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/16/2004 8:30:16 AM  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : DataConnection:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 874  
  
 TEST D'ÉVALUATION DE LA CONDITION (CORRESPONDANCE) 3/16/2004 8:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Expression de test : sélectionnez * à partir de [CustInfo] où [CreditCardBalance] > 0  
  
 Valeur de l'opérande gauche :  
  
 Valeur de l'opérande droit :  
  
 Résultat de test : True  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 177556  
  
 MISE À JOUR DE L'AGENDA 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 177559  
  
 MISE À JOUR DE L'AGENDA 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 177558  
  
 MISE À JOUR DE L'AGENDA 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/16/2004 8:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/16/2004 8:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/16/2004 8:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : DataConnection:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 874  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 177559  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 177558  
  
 ACTIVITÉ DES FAITS 3/16/2004 08:30:16 AM  
  
 Identificateur de l’Instance du moteur de règles : 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 177556  
  
 L'exemple ci-dessous indique que trois lignes de la table CustInfo ont satisfait à la condition de la règle.  Cela a entraîné la déclaration de trois TypedDataRows uniques dans le moteur ainsi qu'une mise à jour de l'agenda et un déclenchement de règle pour chaque instance.  
  
## <a name="typedatatabletypeddatarow"></a>TypeDataTable/TypedDataRow  
 Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 **Sortie :**  
  
 TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/17/2004 11:27:35 : 00  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedDataTable:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 377  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 376  
  
 TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Expression de test : TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 Valeur de l’opérande gauche : 500  
  
 Valeur de l’opérande droite : 0  
  
 Résultat de test : True  
  
 METTRE À JOUR DE AGENDA 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 375  
  
 TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Expression de test : TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 Valeur de l’opérande gauche : 1000  
  
 Valeur de l’opérande droite : 0  
  
 Résultat de test : True  
  
 METTRE À JOUR DE AGENDA 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 374  
  
 TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Expression de test : TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 Valeur de l’opérande gauche : 35000  
  
 Valeur de l’opérande droite : 0  
  
 Résultat de test : True  
  
 METTRE À JOUR DE AGENDA 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedDataTable:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 377  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 375  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 374  
  
 ACTIVITÉ DES FAITS 3/17/2004 11:27:35 : 00  
  
 Identificateur de l’Instance du moteur de règles : 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedDataRow:Northwind:CustInfo  
  
 Identificateur de l’Instance de l’objet : 376  
  
> [!NOTE]
>  L'exemple ci-dessus montre que TypedDataTable contenait trois lignes et que chacune était déclarée en tant que TypedDataRow.  Chacune avait la valeur True dans la condition et a provoqué l'ajout de la règle à l'agenda et son déclenchement.  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 Exemple de la règle « TestRule1 » dans la stratégie « LoanProcessing » :  
  
```  
IF Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4  
THEN <do something>  
```  
  
 **Sortie :**  
  
 TRACE du moteur de règles pour le groupe de règles : LoanProcessing 3/17/2004 9:23:05 AM  
  
 ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM  
  
 Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case  
  
 Identificateur de l’Instance de l’objet : 858  
  
 ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM  
  
 Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : Assert  
  
 Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType  
  
 Identificateur de l’Instance de l’objet : 853  
  
 TEST D'ÉVALUATION DE LA CONDITION (CORRESPONDANCE) 3/17/2004 9:23:05 AM  
  
 Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Nom du groupe de règles : LoanProcessing  
  
 Expression de test : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths > = 4  
  
 Valeur de l’opérande gauche : 6  
  
 Valeur de l’opérande droite : 4  
  
 Résultat de test : True  
  
 MISE À JOUR DE L'AGENDA 3/17/2004 9:23:05 AM  
  
 Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : ajouter  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/17/2004 9:23:05 AM  
  
 Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Nom du groupe de règles : LoanProcessing  
  
 Nom de règle : TestRule1  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM  
  
 Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case  
  
 Identificateur de l’Instance de l’objet : 858  
  
 ACTIVITÉ DES FAITS 3/17/2004 09:23:05 AM  
  
 Identificateur de l’Instance du moteur de règles : 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Nom du groupe de règles : LoanProcessing  
  
 Opération : retrait  
  
 Type d’objet : TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType  
  
 Identificateur de l’Instance de l’objet : 853  
  
 Cet exemple montre qu’un **TypedXmlDocument** a été déclaré dans le moteur avec un type de document de « Microsoft.Samples.BizTalk.LoansProcessor.Case ».  Sur la base du sélecteur XPath défini dans la règle, le moteur a alors créé et déclaré un TypedXmlDocument enfant de type « Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType » basé sur le type du document et la chaîne du sélecteur.  
  
 Ce TypedXmlDocument enfant ayant la valeur True dans la condition, cela a provoqué la mise à jour de l'agenda et le déclenchement de la règle.  Le parent et enfant **TypedXmlDocument**du ont alors été retirés.  
  
## <a name="update-function"></a>Fonction Mise à jour  
 Exemple de stratégie « Order »  
  
 **Règle « InventoryCheck »**  
  
```  
IF Inventory.AllocateInventory == True  
THEN Order.inventoryAvailable == True  
   Update(Order)  
```  
  
 **Règle « Ship »**  
  
```  
IF Order.inventoryAvailable == True  
THEN Shipment.ShipOrder  
```  
  
 **Sortie :**  
  
 TRACE du moteur de règles pour le groupe de règles : commande 3/17/2004 10:31:17 : 00  
  
 ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : Assert  
  
 Type d’objet : TestClasses.Order  
  
 Identificateur de l’Instance de l’objet : 448  
  
 TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Expression de test : TestClasses.Order.inventoryAvailable == True  
  
 Valeur de l’opérande gauche : null  
  
 Valeur de l’opérande droite : True  
  
 Résultat de test : False  
  
 ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : Assert  
  
 Type d’objet : TestClasses.Shipment  
  
 Identificateur de l’Instance de l’objet : 447  
  
 ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : Assert  
  
 Type d’objet : TestClasses.Inventory  
  
 Identificateur de l’Instance de l’objet : 446  
  
 TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Expression de test : TestClasses.Inventory.AllocateInventory == True  
  
 Valeur de l’opérande gauche : True  
  
 Valeur de l’opérande droite : True  
  
 Résultat de test : True  
  
 METTRE À JOUR DE AGENDA 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : ajouter  
  
 Nom de règle : InventoryCheck  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Nom de règle : InventoryCheck  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : mise à jour  
  
 Type d’objet : TestClasses.Order  
  
 Identificateur de l’Instance de l’objet : 448  
  
 TEST D’ÉVALUATION DE CONDITION (CORRESPONDANCE) 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Expression de test : TestClasses.Order.inventoryAvailable == True  
  
 Valeur de l’opérande gauche : True  
  
 Valeur de l’opérande droite : True  
  
 Résultat de test : True  
  
 METTRE À JOUR DE AGENDA 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : ajouter  
  
 Nom de règle : expédition  
  
 Critères de résolution de conflit : 0  
  
 RÈGLE DÉCLENCHÉE 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Nom de règle : expédition  
  
 Critères de résolution de conflit : 0  
  
 ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : retrait  
  
 Type d’objet : TestClasses.Order  
  
 Identificateur de l’Instance de l’objet : 448  
  
 ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : retrait  
  
 Type d’objet : TestClasses.Shipment  
  
 Identificateur de l’Instance de l’objet : 447  
  
 ACTIVITÉ DES FAITS 3/17/2004 10:31:17 : 00  
  
 Identificateur de l’Instance du moteur de règles : 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Nom du groupe de règles : ordre  
  
 Opération : retrait  
  
 Type d’objet : TestClasses.Inventory  
  
 Identificateur de l’Instance de l’objet : 446  
  
 Dans cet exemple, la condition associée à la règle Ship a la valeur False la première fois qu'elle est vérifiée.  Cependant, lorsque la règle InventoryCheck se déclenche, le champ inventoryAvailable de l'Order est modifié et une commande de mise à jour est émise sur le moteur pour l'objet Order.  Cela provoque la réévaluation de la règle Ship.  Cette fois, la condition prend la valeur True et la règle Ship se déclenche.  
  
> [!NOTE]
>  Si vos règles ne sont pas écrites correctement, le chaînage avant avec la fonction Mise à jour risque d'entraîner une boucle infinie.  Lorsque vous testerez la stratégie dans l'Éditeur des règles d'entreprise, vous recevrez dans ce cas un message d'erreur indiquant que le moteur de règles a détecté une boucle d'exécution.