---
title: "L’option transactions &quot;transactionnel&quot; et l’option Gestion d’erreur &quot;suspendre le message de demande en cas d’échec&quot; pas les deux doivent être définies sur false | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc6c66cc-6713-4396-b0d4-ac6a0e72164f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8c47e364fccdb310167e56c6556423c2d4b39d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transactions-option-quottransactionalquot-and-the-error-handling-option-quotsuspend-request-message-on-failurequot-should-not-both-be-set-to-false"></a>L’option transactions &quot;transactionnel&quot; et l’option Gestion d’erreur &quot;suspendre le message de demande en cas d’échec&quot; pas les deux doivent être définies sur false
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|L'option des transactions « Transactionnel » et l'option de gestion des erreurs « Suspendre le message de requête en cas d'échec » ne doivent pas être toutes deux définies sur False, faute de quoi des messages pourraient être perdus. Définissez une ou les deux options à la valeur true.|  
  
## <a name="explanation"></a>Explication  
 Dans l’adaptateur WCF-NetMsmq, les options **transactionnel** et **suspendre le message de demande en cas d’échec** pas les deux doivent être définies sur false (désactivé). Une perte de message peut se produire si l'envoi du message ayant échoué n'a pas été annulé en tant que transaction, alors que le message n'a pas été suspendu ni stocké dans la base de données MessageBox.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de vérifier les paramètres de l'adaptateur.  
  
#### <a name="to-verify-adapter-settings"></a>Pour vérifier les paramètres de l'adaptateur  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.  
  
3.  Recherchez votre application, puis recherchez votre transport.  
  
4.  Cliquez avec le bouton droit sur le nom du transport.  
  
5.  Cliquez sur **Propriétés**.  
  
6.  Dans le port **Type** , sélectionnez le port approprié.  
  
7.  Cliquez sur **configurer**.  
  
8.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, cliquez sur le **liaison** onglet.  
  
9. Dans le **Transactions** section, déterminez si **transactionnel** est activée.  
  
10. Cliquez sur le **Messages** onglet.  
  
11. Déterminer si **suspendre le message de demande en cas d’échec** est activée.  
  
    > [!NOTE]
    >  Ces étapes s'appliquent uniquement aux emplacements de réception.