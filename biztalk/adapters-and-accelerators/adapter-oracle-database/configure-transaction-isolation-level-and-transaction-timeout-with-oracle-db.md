---
title: "Configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b66e764-2330-441b-89ef-29118f27b366
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13d1beea3be34dbd818a94986fb8cae876bcdd81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-transaction-isolation-level-and-transaction-timeout-with-oracle-database"></a>Configurer le niveau d’isolation de transaction et le délai d’attente de transaction avec la base de données Oracle
Lors de l’exécution à l’aide de l’opération entrante (interrogation) le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez configurer correctement le niveau d’isolation de transaction et les valeurs de délai d’attente de transaction. Pour effectuer cette opération :  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez le **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez l’application BizTalk que vous avez déployé après la génération de métadonnées à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
4.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.  
  
5.  Dans le **propriétés du Port de réception** boîte de dialogue le **général** , tapez un nom pour le port de réception.  
  
6.  Dans le volet gauche de la **propriétés du Port de réception** boîte de dialogue, cliquez sur **emplacements de réception**, puis cliquez sur **nouveau** dans le volet droit pour définir un nouvel emplacement de réception.  
  
7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **WCF-Custom** dans les **Type** liste.  
  
8.  Cliquez sur **configurer** adjacente à la **Type** liste.  
  
9. Dans le **propriétés du Transport WCF-Custom** boîte de dialogue, cliquez sur le **comportement** onglet.  
  
10. Dans le **comportement** liste, cliquez sur **ServiceBehavior**, puis cliquez sur **ajouter une extension**.  
  
11. Dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez **oracleDBAdapterInboundTransactionBehavior**, puis cliquez sur **OK**.  
  
12. Dans le volet gauche de la **propriétés du Transport WCF-Custom**, sélectionnez le **oracleDBAdapterInboundTransactionBehavior** service sous **ServiceBehavior**.  
  
13. Dans le volet droit de la **propriétés du Transport WCF-Custom**, spécifiez les valeurs appropriées pour le **transactionIsolationLevel** et **transactionTimeout** paramètres. Vous pouvez choisir parmi les niveaux d’isolation de transaction suivantes : **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Instantané**, **Chaos**, et **non spécifiée**. Pour plus d’informations sur ces niveaux d’isolation des transactions, consultez le **membres** section à [http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983).  
  
    > [!IMPORTANT]
    >  Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge uniquement les niveaux d’isolation des deux transactions suivants : ReadCommitted et Serializable.  
  
     ![Définition du niveau d’Isolation des transactions](../../adapters-and-accelerators/adapter-oracle-database/media/96a66f86-0321-4aa6-9e72-ada30d7de064.gif "96a66f86-0321-4aa6-9e72-ada30d7de064")  
  
14. Cliquez sur **OK** dans les **propriétés du Transport WCF-Custom** boîte de dialogue.  
  
15. Cliquez sur **OK** dans la boîte de dialogue pour enregistrer les modifications.